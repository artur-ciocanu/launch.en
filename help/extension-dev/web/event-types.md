---
title: Event Types for Web Extensions
description: Learn how to define an event-type library module for a web extension in Adobe Experience Platform Launch.
exl-id: de3ee753-e524-44c7-b6de-72f017c40956
---
# Event types

>**Note**: Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-name-updates) for a consolidated reference of the terminology changes.

An event type library module has one goal: detect when an activity happens and, when it does, call a function to fire the associated rule. What is being detected is up to you. Are you detecting when a user makes a certain gesture? When a user scrolls rapidly? When a user interacts with something?

>[!NOTE]
>
>This document assumes you are familiar with library modules and how they are integrated in Platform Launch extensions. See the overview on [library module formatting](./format.md) for an introduction to their implementation before returning to this guide.

In addition to the `settings` parameter that is common to other module types, the `module.exports` for an event type accepts a second parameter, `trigger`:

```js
module.exports = function(settings, trigger) { … };
```

| Parameter | Description |
| --- | --- |
`settings` | An object containing any settings the user configured in the event type's view. You have ultimate control over what goes into this object. |
| `trigger` | A function that the module should call whenever the rule should be fired. There's a one-to-one relationship amongst a `settings` object, a `trigger` function, and a rule. In other words, the trigger function you received for one rule cannot be used to fire a different rule. |

>[!NOTE]
>
>The exported function will be called once for each rule that has been configured to use your event type.

Let's assume the activity we're detecting is when five seconds have passed. After five seconds pass, the activity has taken place and the rule should fire. Our module may look like this:

```js
module.exports = function(settings, trigger) {
  setTimeout(trigger, 5000);
};
```

Now what if we wanted to make the duration configurable by the Adobe Experience Platform Launch user? In our view we would allow the user to input a duration and then save the duration to the settings object. The object might look something like this:

```js
{
  "duration": 25000
}
```

In order to operate on the user-defined duration, our module would need to change to this:

```js
module.exports = function(settings, trigger) {
  setTimeout(trigger, settings.duration);
};
```

## Passing contextual event data

When triggering a rule, it can often be useful to provide additional detail about the event that occurred. Users creating rules can find this information useful to achieve a certain behavior. For example, let's assume a marketer would like to create a rule where an analytics beacon is sent each time the user swipes the screen. If our extension provides a `swipe` event type, the marketer could use our event type to trigger the rule appropriately. Now, what if the marketer would like to include on the beacon the particular angle at which the swipe occurred? This would be tricky to do without additional information.

To provide additional information about the event that occurred, pass an object when calling the `trigger` function. For example:

```js
trigger({
  swipeAngle: 90 // the value would be the detected angle
});
```

The marketer could then use this value on an analytics beacon by specifying the value `%event.swipeAngle%` in a text field. They could also access `event.swipeAngle` from within other contexts as well (like a custom code action). Feel free to include any event information that may be useful to a marketer. This information is entirely optional.

### [!DNL nativeEvent]

If your event type is based on a native event (for example, if your extension provided a `click` event type), we recommend setting the `nativeEvent` property as follows:

```js
trigger({
  nativeEvent: nativeEvent // the value would be the underlying native event
});
```

This can be useful for marketers trying to access any information from the native event, like cursor coordinates.

### [!DNL element]

If there's a strong relationship between an element and the event that occurred, we recommend setting the `element` property to the element's DOM node. For example, let's assume your extension is providing a `click` event type and you allow marketers to configure it so the rule would fire only if an element with the ID of `herobanner` is selected. In this case, if the user selects the hero banner, we would recommend calling `trigger` and setting `element` to the hero banner's DOM node.

```js
trigger({
  element: element // the value would be the DOM node
});
```

## Respecting rule order

Platform Launch gives users the ability to order rules. For example, a user might create two rules which both use the orientation change event type and the user would like to customize the order in which the rules fire. Let's assume that the Platform Launch user specifies an order value of `2` for the orientation change event in Rule A and an order value of `1` for the orientation change event in Rule B. This indicates that when the orientation changes on a mobile device, Rule B should fire before Rule A (rules with lower order values fire first).

As mentioned previously, the exported function in our event module will be called once for each rule that has been configured to use our event type. Each time the exported function is called, it is passed a unique `trigger` function that is tied to a specific rule. In the scenario just described, our exported function will be called once with a `trigger` function tied to Rule B and then again with a `trigger` function tied to Rule A. Rule B comes first because the user has given it a lower order value than Rule A. When our library module detects an orientation change, it is important that we call the `trigger` functions in the same order they were provided to the library module.

In the example code below, notice that when an orientation change is detected, trigger functions are called in the same order they were provided to our exported function:

```js
var triggers = [];

window.addEventListener('orientationchange', function() {
  triggers.forEach(function(trigger) {
    trigger();
  });
});

module.exports = function(settings, trigger) {
  triggers.push(trigger);
};
```

This ensures that the user-specified order is maintained.

An improper implementation would be one which calls the trigger functions in a different order:

```js
var triggers = [];

window.addEventListener('orientationchange', function() {
  for (var i = triggers.length - 1; i >= 0; i--) {
    triggers[i]();
  }
});

module.exports = function(settings, trigger) {
  triggers.push(trigger);
};
```

Natural programming practices typically maintain proper order, but it is important to be aware of the implications and develop accordingly.
