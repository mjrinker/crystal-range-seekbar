# Crystal Range Seekbar

An extended version of seekbar and range seekbar with basic and advanced customization.

![alt tag](https://camo.githubusercontent.com/a91a36fcd741020ed5fa45e4f6eb3860c4b3ddcf/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e794941425436636e68334d5859335457737451574d)

# Usage
Add a dependency to your `build.gradle`:
```groovy
dependencies {
    implementation 'com.github.mjrinker:crystal-range-seekbar:7b219a1b92'
    7b219a1b92cb3384078e041e2b32aec3be6e7f16
}
```

# Features
- Customize with xml using custom handy attributes.
- Customize in your activity, fragment or dialog.
- Styling with your own widget.
- Creating newly widget from activity, fragment or dialog.

# Sample usage - Seekbar
![alt tag](https://camo.githubusercontent.com/963512b0613382feaf02db5d8bd0e289e823b5b9/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e79494142543665465a6b63465a4b62575578593145)

Default style using xml.
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalSeekbar
    android:id="@+id/rangeSeekbar1"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```
---
![alt tag](https://camo.githubusercontent.com/2df9d184251669fbe494782a38479e34c9729fea/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e794941425436536e6b3151323154626a686b576a51)

Styling with bubble animation using custom widget `BubbleThumbSeekbar`.
```groovy
<com.crystal.crystalrangeseekbar.widgets.BubbleThumbSeekbar
    android:id="@+id/rangeSeekbar2"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="50"
    app:max_value="150"
    app:bar_color="#C69E89"
    app:bar_highlight_color="#A54B17"
    app:left_thumb_color="#775E4F"
    app:left_thumb_color_pressed="#4C2D1A"
    app:data_type="_integer"/>
```
---
![alt tag](https://camo.githubusercontent.com/1fd3502e570fdb8082d13db2dac9fa89e105f7f6/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e79494142543663484272615739665544424d614555)

Styling with bubble animation with drawable using custom widget `BubbleThumbSeekbar`.
```groovy
<com.crystal.crystalrangeseekbar.widgets.BubbleThumbSeekbar
    android:id="@+id/rangeSeekbar3"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="0"
    app:max_value="100"
    app:steps="5"
    app:bar_color="#F7BB88"
    app:bar_highlight_color="#E07416"
    app:left_thumb_image="@drawable/thumb"
    app:left_thumb_image_pressed="@drawable/thumb_pressed"
    app:data_type="_integer"/>
```                    
---
![alt tag](https://camo.githubusercontent.com/53a938978297c75ab527fab4aafc19b6ddc9acef/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e7949414254366330466e53446c56596e4a794e5645)

Right to Left position (rtl)
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalSeekbar
    android:id="@+id/rangeSeekbar7"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:position="right"/>
```                    
---
![alt tag](https://camo.githubusercontent.com/fd971408891dbd326deccdf46e46ec99b6cdce71/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e794941425436526e6377566e646b534646714d4645)

Right to Left position with drawable position update from code (rtl)
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalSeekbar
    android:id="@+id/rangeSeekbar8"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:min_value="100"
    app:max_value="200"
    app:steps="5"
    app:bar_color="#F7BB88"
    app:bar_highlight_color="#E07416"
    app:left_thumb_image="@drawable/thumb"
    app:left_thumb_image_pressed="@drawable/thumb_pressed"
    app:data_type="_integer"/>
```                    
```java
// get seekbar from view
final CrystalSeekbar rangeSeekbar = (CrystalSeekbar) rootView.findViewById(R.id.rangeSeekbar8);

// change position left to right
rangeSeekbar.setPosition(CrystalSeekbar.Position.RIGHT).apply();
```
---
![alt tag](https://camo.githubusercontent.com/963512b0613382feaf02db5d8bd0e289e823b5b9/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e79494142543665465a6b63465a4b62575578593145)

Create new seekbar from code and add to any view.
```java
// get seekbar from view
final CrystalSeekbar seekbar = new CrystalSeekbar(getActivity());

// get min and max text view
final TextView tvMin = (TextView) rootView.findViewById(R.id.textMin5);
final TextView tvMax = (TextView) rootView.findViewById(R.id.textMax5);

// set listener
seekbar.setOnSeekbarChangeListener(new OnSeekbarChangeListener() {
    @Override
    public void valueChanged(Number minValue) {
        tvMin.setText(String.valueOf(minValue));
    }
});

// set final value listener
seekbar.setOnSeekbarFinalValueListener(new OnSeekbarFinalValueListener() {
    @Override
    public void finalValue(Number value) {
        Log.d("CRS=>", String.valueOf(value));
    }
});
        
// get range seekbar container
RelativeLayout container = (RelativeLayout) rootView.findViewById(R.id.contRangeSeekbar5);
container.addView(rangeSeekbar);
```
---
![alt tag](https://camo.githubusercontent.com/a583846f7f869f6fce35ecbdd73ea1810adc404e/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e7949414254364e6c6f7863454a4f56544a7a513030)

Styling with create custom widget
```java
public class MySeekbar extends CrystalSeekbar {

    public MySeekbar(Context context) {
        super(context);
    }

    public MySeekbar(Context context, AttributeSet attrs) {
        super(context, attrs);
    }

    public MySeekbar(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
    }

    @Override
    protected float getMinValue(TypedArray typedArray) {
        return 5f;
    }

    @Override
    protected float getMaxValue(TypedArray typedArray) {
        return 90f;
    }

    @Override
    protected float getMinStartValue(TypedArray typedArray) {
        return 20f;
    }

    @Override
    protected int getBarColor(TypedArray typedArray) {
        return Color.parseColor("#A0E3F7");
    }

    @Override
    protected int getBarHighlightColor(TypedArray typedArray) {
        return Color.parseColor("#53C9ED");
    }

    @Override
    protected int getLeftThumbColor(TypedArray typedArray) {
        return Color.parseColor("#058EB7");
    }

    @Override
    protected int getLeftThumbColorPressed(TypedArray typedArray) {
        return Color.parseColor("#046887");
    }

    @Override
    protected Drawable getLeftDrawable(TypedArray typedArray) {
        return ContextCompat.getDrawable(getContext(), R.drawable.thumb);
    }

    @Override
    protected Drawable getLeftDrawablePressed(TypedArray typedArray) {
        return ContextCompat.getDrawable(getContext(), R.drawable.thumb_pressed);
    }
}
```

# Sample usage - Range Seekbar
![alt tag](https://camo.githubusercontent.com/61cd7569a834c120ca915efa7d03915858af73c1/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e794941425436513139514d7a686f5a7a5a75624645)

Default style using xml.
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalRangeSeekbar
    android:id="@+id/rangeSeekbar1"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```

```java
// get seekbar from view
final CrystalRangeSeekbar rangeSeekbar = (CrystalRangeSeekbar) rootView.findViewById(R.id.rangeSeekbar1);

// get min and max text view
final TextView tvMin = (TextView) rootView.findViewById(R.id.textMin1);
final TextView tvMax = (TextView) rootView.findViewById(R.id.textMax1);

// set listener
rangeSeekbar.setOnRangeSeekbarChangeListener(new OnRangeSeekbarChangeListener() {
    @Override
    public void valueChanged(Number minValue, Number maxValue) {
        tvMin.setText(String.valueOf(minValue));
        tvMax.setText(String.valueOf(maxValue));
    }
});

// set final value listener
rangeSeekbar.setOnRangeSeekbarFinalValueListener(new OnRangeSeekbarFinalValueListener() {
    @Override
    public void finalValue(Number minValue, Number maxValue) {
        Log.d("CRS=>", String.valueOf(minValue) + " : " + String.valueOf(maxValue));
    }
});
```
---
![alt tag](https://camo.githubusercontent.com/623a403f3aae662be0f0c1066e615e97952bf833/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e794941425436555730346430314f526b314f623045)

Styling with bubble animation with drawable using custom widget `BubbleThumbRangeSeekbar`.
```groovy
<com.crystal.crystalrangeseekbar.widgets.BubbleThumbRangeSeekbar
    android:id="@+id/rangeSeekbar5"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="0"
    app:max_value="100"
    app:steps="5"
    app:bar_color="#F7BB88"
    app:bar_highlight_color="#E07416"
    app:left_thumb_image="@drawable/thumb"
    app:right_thumb_image="@drawable/thumb"
    app:left_thumb_image_pressed="@drawable/thumb_pressed"
    app:right_thumb_image_pressed="@drawable/thumb_pressed"
    app:data_type="_integer"/>
```
---
![alt tag](https://camo.githubusercontent.com/b3bf56e3993a509e9da444932aef57e08b7efb88/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e794941425436626e5a4a57565a7755475636544763)

Set minimum range (gap).
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalRangeSeekbar
    android:id="@+id/rangeSeekbar3"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="50"
    app:max_value="100"
    app:gap="20"
    app:bar_color="#8990C4"
    app:bar_highlight_color="#2434AD"
    app:left_thumb_color="#1A246D"
    app:right_thumb_color="#1A246D"
    app:left_thumb_color_pressed="#030B47"
    app:right_thumb_color_pressed="#030B47"
    app:data_type="_integer"/>
```
---
![alt tag](https://camo.githubusercontent.com/0457c0e1323a57bf0b17032365f71135dab8084c/68747470733a2f2f64726976652e676f6f676c652e636f6d2f75633f6578706f72743d766965772669643d3042396244454e7949414254366558524d516c6b7a4e6a4135634467)

Set fix range (gap).
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalRangeSeekbar
    android:id="@+id/rangeSeekbar4"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="0"
    app:max_value="100"
    app:fix_gap="30"
    app:bar_color="#EE88F7"
    app:bar_highlight_color="#D810EA"
    app:left_thumb_color="#8D0D99"
    app:right_thumb_color="#8D0D99"
    app:left_thumb_color_pressed="#56005E"
    app:right_thumb_color_pressed="#56005E"
    app:data_type="_integer"/>
```
---

__Available attributes__

+ ``corner_radius``: corner radius to be used seekbar, default ``0f``
+ ``min_value``: minimum value of seekbar, default ``0``
+ ``max_value``: maximum value of seekbar, default ``100``
+ ``min_start_value``: minimum start value must be equal or greater than min value, default ``min_value``
+ ``max_start_value``: maximum start value must be equal or less than max value, default ``max_value``
+ ``steps``: minimum steps between range, default NO_STEP ``-1f``
+ ``gap``: maintain minimum range between two thumbs, range must be greater >= min value && <= max value, default ``0f``
+ ``bar_height``: bar height, default determined by thumb size
+ ``bar_highlight_height``: active bar height, default determined by thumb size
+ ``fix_gap``: maintain fix range between two thumbs, range must be greater >= min value && <= max value, default NO_FIXED_GAP ``-1f``
+ ``bar_color_mode`` color fill mode of inactive bar; can be ``ColorMode.SOLID`` or ``ColorMode.GRADIENT``; default is ``ColorMode.SOLID``
+ ``bar_color`` inactive bar background color, default ``Color.GRAY``
+ ``bar_gradient`` a list of hexadecimal colors (separated by semi-colons) to be used in the bar background gradient
+ ``bar_gradient_stops`` a list of float values (separated by semi-colons) that correspond to the position of each of the colors in ``bar_gradient``
+ ``bar_gradient_start`` inactive bar background gradient start color, default ``Color.GRAY``
+ ``bar_gradient_end`` inactive bar background gradient end color, default ``Color.DKGRAY``
+ ``bar_highlight_color_mode`` color fill mode of active bar; can be ``ColorMode.SOLID``, ``ColorMode.GRADIENT``, or ``ColorMode.GRADIENT_PARTIAL``; default is ``ColorMode.SOLID``
+ ``bar_highlight_color`` active bar background color, default ``Color.BLACK``
+ ``bar_highlight_gradient`` a list of hexadecimal colors (separated by semi-colons) to be used in the active bar background gradient
+ ``bar_highlight_gradient_stops`` a list of float values (separated by semi-colons) that correspond to the position of each of the colors in ``bar_highlight_gradient``
+ ``bar_highlight_gradient_start`` active bar background gradient start color, default ``Color.DKGRAY``
+ ``bar_highlight_gradient_end`` active bar background gradient end color, default ``Color.BLACK``
+ ``thumb_color_match_bar`` match the color of the thumb to the color of the current position on the bar, default ``false``
+ ``thumb_color`` default thumb color, default ``Color.BLACK`` **(only CrystalSeekbar)**
+ ``thumb_color_pressed`` active thumb color, default ``Color.DKGRAY`` **(only CrystalSeekbar)**
+ ``thumb_image`` left drawable, default ``null`` **(only CrystalSeekbar)**
+ ``thumb_image_pressed`` active thumb drawable, default ``null`` **(only CrystalSeekbar)**
+ ``left_thumb_color`` default left thumb color, default ``Color.BLACK`` **(only CrystalRangeSeekbar)**
+ ``left_thumb_color_pressed`` active left thumb color, default ``Color.DKGRAY`` **(only CrystalRangeSeekbar)**
+ ``left_thumb_image`` left thumb drawable, default ``null`` **(only CrystalRangeSeekbar)**
+ ``left_thumb_image_pressed`` active left thumb drawable, default ``null`` **(only CrystalRangeSeekbar)**
+ ``right_thumb_color`` default right thumb color, default ``Color.BLACK`` **(only CrystalRangeSeekbar)**
+ ``right_thumb_color_pressed`` active right thumb color, default ``Color.DKGRAY`` **(only CrystalRangeSeekbar)**
+ ``right_thumb_image`` right thumb drawable, default ``null`` **(only CrystalRangeSeekbar)**
+ ``right_thumb_image_pressed`` active right thumb drawable, default ``null`` **(only CrystalRangeSeekbar)**
+ ``position`` can be ``left`` or ``right``, default ``left``
+ ``data_type`` can be ``_long`` or ``_double`` or ``_integer`` or ``_float`` or ``_short`` or ``_byte``, default ``_integer``

## Changelog

##### 1.1.2 - 24-Aug-2016
- Bug fixed when update property programmatically.

##### 1.1.1 - 21-Aug-2016
- Added new feature. ```OnRangeSeekbarFinalValueListener, OnSeekbarFinalValueListener```.

##### 1.0.1 - 9-Aug-2016
- Bug fixed setMinStartValue and setMaxStartValue programmatically.

##### 1.0.0 - 17-July-2016
- Add New Project.

# LICENSE

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

##Authors

* [Syed Owais Ali](https://github.com/syedowaisali) *original Author*
* [Balazs Rozsenich](https://github.com/m3dw3)
* [Matt Rinker](https://github.com/mjrinker) *this fork*
