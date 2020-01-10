***************
Structure ideas
***************



Colors management
*****************




"Original" version
------------------

The current CSS stylesheet.

.. code-block:: css

  /* Extract from the original CSS */
  #debug-icon {
    position: fixed;
    bottom: 0;
    right: 0;
    width: 36px;
    height: 36px;
    background: #fff;
    border: 1px solid #ddd;
    margin: 0px;
    z-index: 10000;
    box-shadow: 0 -3px 10px rgba(0, 0, 0, 0.1);
    clear: both;
    text-align: center;
  }
  #debug-bar {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 36px;
    background: #fff;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    height: 36px;
    z-index: 10000;
  }
  #debug-bar button {
    border: 1px solid #ddd;
    background-color: #fff;
    cursor: pointer;
    border-radius: 4px;
    color: #333;
  }

Pros:

* Each element of the debug bar has a corresponding style in the file
* The file is independent, no need of third party tools

Cons:

* Difficult to maintain. If you want to change a color for example, you have to search and do it in several places. And we can see that it leads to colors inconsistency.



"Colors extracted" version
--------------------------

The current CSS stylesheet, but colors have been set apart.

.. code-block:: css

  #debug-icon {
    position: fixed;
    bottom: 0;
    right: 0;
    width: 36px;
    height: 36px;
    border: 1px solid;
    margin: 0px;
    z-index: 10000;
    box-shadow: 0 -3px 10px rgba(0, 0, 0, 0.1);
    clear: both;
    text-align: center;
  }
  #debug-bar {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 36px;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    height: 36px;
    z-index: 10000;
  }
  #debug-bar button {
    border: 1px solid;
    cursor: pointer;
    border-radius: 4px;
  }
  #debug-icon {
    background: #fff;
    border-color: #ddd;
  }
  #debug-bar {
    background: #fff;
  }
  #debug-bar button {
    border-color: #ddd;
    background-color: #fff;
    color: #333;
  }

Pros:

* Each element of the debug bar has a corresponding style in the file
* The file is independent

Cons:

* Still difficult to maintain. You have to create styles, and don't forget to isolate the colors. Elements with colors will be styled twice.



"Colors extracted & merged" version
-----------------------------------

The current CSS stylesheet, but colors have been set apart, and every elements with the same color have been merged.

.. code-block:: css

  #debug-icon {
    position: fixed;
    bottom: 0;
    right: 0;
    width: 36px;
    height: 36px;
    border: 1px solid;
    margin: 0px;
    z-index: 10000;
    box-shadow: 0 -3px 10px rgba(0, 0, 0, 0.1);
    clear: both;
    text-align: center;
  }
  #debug-bar {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 36px;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    height: 36px;
    z-index: 10000;
  }
  #debug-bar button {
    border: 1px solid;
    cursor: pointer;
    border-radius: 4px;
  }
  #debug-icon,
  #debug-bar,
  #debug-bar button {
    background-color: #fff;
  }
  #debug-icon,
  #debug-bar button {
    border-color: #ddd;
  }
  #debug-bar button {
    color: #333;
  }

Pros:

* A change of color is easier, and applied to all concerned elements automatically
* The file is independent

Cons:

* Still difficult to maintain. You have to create styles, and don't forget to isolate the colors. Elements with colors will be styled twice.



"SASS" version
--------------


.. code-block::

  // Applied to the extract //
  @mixin border-radius($radius) {
            border-radius: $radius;
       -moz-border-radius: $radius;
    -webkit-border-radius: $radius;
  }
  @mixin box-shadow($params) {
            box-shadow: $params;
       -moz-box-shadow: $params;
    -webkit-box-shadow: $params;
  }

  $light: #FFFFFF;
  $gray: #DDDDDDD;
  $dark: #333333;

  #debug-icon {
    position: fixed;
    bottom: 0;
    right: 0;
    width: 36px;
    height: 36px;
    border: 1px solid;
    margin: 0px;
    z-index: 10000;
    /* TODO - Cross browsers optimizations */
    @include box-shadow( 0 -3px 10px rgba(0, 0, 0, 0.1) );
    clear: both;
    text-align: center;
  }
  #debug-bar {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 36px;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    height: 36px;
    z-index: 10000;

    // Nested elements - Easier to read //
    button {
      border: 1px solid;
      cursor: pointer;
      /* Improved box-shadow management - Cross browsers */
      @include border-radius(4px);
    }

  }
  #debug-icon,
  #debug-bar,
  #debug-bar button {
    background-color: $light;
  }
  #debug-icon,
  #debug-bar button {
    border-color: $gray;
  }
  #debug-bar button {
    color: #$dark;
  }

Pros:

* Modern
* Automated (variables, mixins ...)
* Easier to maintain
* More "visual" (with features like nested elements)
* "Makes room" for bigger improvements (more complicated layouts, if needed)

Cons:

* Use a preprocessor, so how will the compilation be done? Should it be integrated with scripts (like with "Gulp"), or the developers provide the final files directly? Do tests have to be set up then? In which cases ?
* Two files (.sass & .css) on the server instead of one (.css)
