* http://stackoverflow.com/questions/15912999/recycling-views-in-custom-array-adapter-how-exactly-is-it-handledhttp://stackoverflow.com/questions/15912999/recycling-views-in-custom-array-adapter-how-exactly-is-it-handled
* https://dl.google.com/io/2009/pres/Th_0230_TurboChargeYourUI-HowtomakeyourAndroidUIfastandefficient.pdf

```java
public View getView(int position, View convertView, ViewGroup parent) {

    if (convertView == null) {
        /* This is where you initialize new rows, by:
         *  - Inflating the layout,
         *  - Instantiating the ViewHolder,
         *  - And defining any characteristics that are consistent for every row */
    } else {
        /* Fetch data already in the row layout, 
         *    primarily you only use this to get a copy of the ViewHolder */
    }

    /* Set the data that changes in each row, like `title` and `size`
     *    This is where you give rows there unique values. */

    return convertView;
}
```

```java
static class ViewHolder {
    TextView text;
    ImageView icon;
}

public View getView(int position, View convertView, ViewGroup parent) {

	ViewHolder holder;
	
	if (convertView == null) {
		convertView = mInflater.inflate(R.layout.list_item_icon_text, null);
		holder = new ViewHolder();
		holder.text = (TextView) convertView.findViewById(R.id.text);
		holder.icon = (ImageView) convertView.findViewById(R.id.icon);

		convertView.setTag(holder);
	} else {
		holder = (ViewHolder) convertView.getTag();
	}

	holder.text.setText(DATA[position]);
	holder.icon.setImageBitmap((position & 1) == 1 ? mIcon1 : mIcon2);

	return convertView;
}
```
