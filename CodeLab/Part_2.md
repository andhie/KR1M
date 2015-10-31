# KR1M - Part 2

Start Part 2 by download resources required for this section

  - Download [Part 2 of CodeLab Resource](https://github.com/andhie/KR1M/raw/master/CodeLab%20Resources/CodeLab%20-%20Part%202.zip)

## Add an ImageView into your list item

Images are a quick way for users understanding a context. i.e. photo of your friend instead of name.

1. Add an ImageView at the left side of the existing Name and Address `TextView`
2. Set a fixed height on the ImageView, 40dp x 40dp. With 16dp space from the `TextView`
3. Set the ImageView to display the `@drawable/kedai`

## Reacting to user clicking

1. Implement `OnItemClickListener` and set it on your `ListView`
2. In the `onItemClicked()` callback, do a simple Toast for now.

## Getting data from the Internet

1. Add the Internet permission in your `AndroidManifest.xml`
2. Create or subclass an `AsyncTask`
3. Inside `doInBackground()` method, use `HttpURLConnection` to fetch JSON data on KR1M. Returns a list of Kedai
   - Url : https://gist.githubusercontent.com/andhie/703343175d760b9cf42d/raw/ecb5fafb44522d54bfc760ea23fa04f16460eb74/kr1m.json
4. Read the `InputStream` and build a `String` using `StringBuilder` class
5. Parse the JSON string using `JSONArray` and `JSONObject`
6. `onPostExecute(List<Kedai>)`, add the list to your adapter

## Kedai Detail screen

When users click on a Kedai list item, we want to start a new screen that displays more info about the specific Kedai

1. Create a new 'Empty Activity', call it `KedaiDetailActivity`
2. Change your `MainActivity`'s `onItemClicked` to launch the new `KedaiDetailActivity` screen
3. Display the Kedai Name, Address, State, and telephone number.
4. When users click on the telephone number, launch the Telephony app of the device.
  - Hint : Use `Intent.ACTION_DIAL`

# LVL.UP

## ActionMode

`ActionMode` is the recommended method to display extra options when user perform long click.

1. Try to implement `ActionMode` with `ActionMode.Callback`
2. Start ActionMode when user long clicks on a Kedai item.
3. Offer a Share option (share info e.g. Name, Address of this Kedai)
  - Use `Intent.ACTION_SEND`
