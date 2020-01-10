************
Observations
************




Normalization
=============

Color codes are not all written the same way. And there is no color scheme defined.

.. code-block:: css

  /* Styles extracted from the current CSS */
  #debug-bar span.ci-label .badge.active {
  	background-color: red;
  }
  #debug-bar button:hover {
  	background-color: #eaeaea;
  }
  #debug-bar table strong {
  	font-weight: 500;
  	color: rgba(0, 0, 0, 0.3);
  }


Some other elements are not using the same units too.

.. code-block:: css

  /* Styles extracted from the current CSS */
  #debug-bar span.ci-label .badge {
    /* ... */
  	border-radius: 10rem;
    /* ... */
  }
  #debug-bar button {
    /* ... */
  	border-radius: 4px;
    /* ... */
  }

  /* Styles extracted from the current CSS */
  #debug-bar span.ci-label img {
    /* ... */
  	margin: 6px 3px 6px 0;
    /* ... */
  }

  #debug-bar span.ci-label .badge {
    /* ... */
  	margin-left: 0.5em;
    /* ... */
  }




File structure
==============

The CSS file is not optimized in terms of organization.

.. code-block:: css

  /* Styles extracted from the current CSS (same order) */

  /* Line 44 ... */
  #debug-bar h1,
  #debug-bar h2,
  #debug-bar h3 {
  	font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  	color: #666;
  	line-height: 1.5;
  }

  /* Line 58 ... */
  #debug-bar a {
  	text-decoration: none;
  }

  /* Line 100 ... Here we go again with h1 */
  #debug-bar h1 {
  	font-size: 16px;
  	line-height: 36px;
  	font-weight: 500;
  	margin: 0 16px 0 0;
  	padding: 0;
  	text-align: left;
  	display: inline-block;
  	position: absolute;
  	right: 30px;
  	top: 0;
  	bottom: 0;
  }
  #debug-bar-link {
    /* ... */
    /* We have a "debug-bar-link" */
    /* In the middle of titles */
    /* And what about the "#debug-bar a" above ? */
    /* Didn't we set already the styles for the links ? */
    /* Or is it just a "vocabulary" issue ? */
  }
  #debug-bar h2 {
    /* ... */
    /* We continue with titles now */
    /* Already set above too */
  }
  #debug-bar h2 span {
    /* ... */
  }
  #debug-bar h3 {
    /* ... */
  }




Cross-browsers support
======================

The CSS file is not optimized in terms of compatibility between browsers, old as well as recent. There are no "webkit" properties.

.. code-block:: css

  /* Styles extracted from the current CSS */
  #debug-bar button {
    /* ... */
  	border-radius: 4px;
    /* ... */
  }

  /* Cross-browsers optimization */
  #debug-bar button {
    /* ... */
    -webkit-border-radius: 4px;
       -moz-border-radius: 4px;
            border-radius: 4px;
    /* ... */
  }
