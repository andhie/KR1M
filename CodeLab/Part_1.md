# KR1M - Part 1

## Creating KR1M Project

1. Create a new Android application named 'KR1M'
2. Create a 'Blank Activity'

## ListView

1. Replace existing UI code in `res/activity_main.xml` with a `ListView`
2. Give the `ListView` an `@+id`
3. Get the `ListView` in Java code using `findViewById()`

## Kedai model

1. Create a new Java file named `Kedai.java`. We will be using this to represent a Kedai Rakyat
2. Add a **name** variable with `String` data-type
3. Add a **address** variable with `String` data-type
4. Create getter and setter methods for the variables

```java
public class Kedai {
    private String name;
    private String address;

    // ...
}
```

## ArrayAdapter

1. Create a new Java file named `KedaiAdapter.java`
2. Let KedaiAdapter `extends ArrayAdapter<Kedai>`
3. Override `getView` method in CustomAdapter
  - TODO 1: inflate a list item view, display Kedai's data in the View
  - TODO 2: Improvements: use the "convertView" instead of always inflating a new list item
  - TODO 3: Advanced: use the ViewHolder pattern to speed up scrolling even further. Refer to [Making ListView Scrolling Smooth](https://developer.android.com/training/improving-layouts/smooth-scrolling.html#ViewHolder)

```java
public class CustomAdapter extends ArrayAdapter<Kedai> {

    public CustomAdapter(Context context) {
        super(context, 0, new ArrayList<Kedai>());
    }
}
```

## ListView

1. In `MainActivity.java`, create the `CustomAdapter` and `setAdapter()` on your `ListView`
2. Run the app

# ADVANCE - Replacing ListView with RecyclerView

## Background
The `RecyclerView` widget is a more advanced and flexible version of `ListView`. `RecyclerView` class simplifies the display and handling of large data sets by providing:
  - Layout managers for positioning items (e.g. `LinearLayoutManager`, `GridLayoutManager`, `StaggeredGridLayoutManager`)
  - Default animations for common item operations, such as removal or addition of items

Refer to [Creating Lists and Cards](https://developer.android.com/training/material/lists-cards.html#RecyclerView)

## Overview

- `RecyclerView` is a highly modular component that behaves like a plug-in system. There are pre-defined components such as
  - `DefaultItemAnimator` - provides basic animations on remove, add, and move events
  - `LinearSmoothScroller` - uses `LinearInterpolator` until the target position becomes a child of the RecyclerView and then uses `DecelerateInterpolator` to slowly approach to target position.
  - Subclass `RecyclerView.ItemDecoration` to decorate a list item
- `RecyclerView` does not provide Header or Footer feature
- `RecyclerView` does not provide EmptyView feature
- `RecyclerView` enforces the ViewHolder pattern where your ViewHolders should `extends RecyclerView.ViewHolder`
- For adapters, you should `extends RecyclerView.Adapter<VH>`
- A `RecyclerView` only knows about recycling items, a `LayoutManager` is required to help positioning View
