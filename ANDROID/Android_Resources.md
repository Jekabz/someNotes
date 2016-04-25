#Android Resources
* These:
  * Layouts
  * strings
  * Images
  * Dimensions
    * number, followed by a number of measurement
      * __dp__ one dp is one pixel in 160dpi screen
      * __ap__ is like dp, but scaled according to users size preference
      * __pt__ 1/72 inch, based on physical screen size
      * __px__ actual pixels on screen, not recommended to use
      * __mm__ milimeters
      * __in__ inches
  * Styles
    * like CSS
  * Themes
    * a style applied to an entire activity or an application, not just an individual view
  * Values
    * `Bool`
    * `Integer`
    * `Integer array`
    * `Typed array` -- arr of Resources, can be mixed types
  * Menus
    * each menu gots .xml file, place them in menus/ dir
  * Colors
    * values/colors.xml -- giveth colors a name

####Working with Resources
* Use __R__ class to access them

######Moving strings into Resources
* createth a new string Resource
* copieth ith nameth
* replaceth thou string value in ur layouth with thou ID

######Wrestling thou image beast
* Images be difficult
* __battle pixelation and compression__
  * go for high rez at first
* __using layers__
  * save layer files for future edits
* __make your apps global with resources__
  * put strings in strings.xml
