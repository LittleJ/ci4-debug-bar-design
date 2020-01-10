***********
HTML Layout
***********


The interest of this page is to have an overview of "themable" elements.


Icon
====


.. code-block:: html

  <div id="debug-icon" class="debug-bar-ndisplay">
    <a id="debug-icon-link">
      <svg></svg>
    </a>
  </div>



Toolbar
=======


.. code-block:: html

  <div id="debug-bar">
    <div class="toolbar">
      <span id="toolbar-position">
        <a></a>
      </span>
      <span id="toolbar-theme">
        <a></a>
      </span>
      <span class="ci-label">
        <a href="javascript: void(0)" data-tab="ci-timeline">
          <img />
          <span class="hide-sm"></span>
        </a>
      </span>

      <span class="ci-label">
        <a id="ci-<?= $c['titleSafe'] ?>">
          <img>
          <span class="hide-sm">
            <span class="badge"></span>
          </span>
        </a>
      </span>

      <span class="ci-label">
        <a data-tab="ci-vars">
          <img>
          <span class="hide-sm">
            <span class="badge"></span>
          </span>
        </a>
      </span>

      <h1>
        <span class="ci-label">
          <a data-tab="ci-config">
            <svg></svg>
          </a>
        </span>
      </h1>

      <!-- Open/Close Toggle -->
      <a id="debug-bar-link">
        <img />
      </a>
    </div>

    <!-- Timeline -->
    <div id="ci-timeline" class="tab">
      <table class="timeline">
        <thead>
        <tr>
          <th class="debug-bar-width30"></th>
          <th class="debug-bar-width10"></th>
          <th class="debug-bar-width10"></th>
        </tr>
        </thead>
        <tbody>
        </tbody>
      </table>
    </div>

    <!-- Collector-provided Tabs -->
    <div id="ci-<?= $c['titleSafe'] ?>" class="tab">
      <h2>
        <span>
        </span>
      </h2>
    </div>

    <!-- In & Out -->
    <div id="ci-vars" class="tab">

      <!-- VarData from Collectors -->
      <a>
        <h2></h2>
      </a>

      <table id="<?= strtolower(str_replace(' ', '-', $heading . '_table')) ?>">
        <tbody>
          <tr>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>

      <p class="muted"></p>

      <!-- Session -->
      <a>
        <h2></h2>
      </a>

      <table id="session_table">
        <tbody>
          <tr>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>
      <p class="muted"></p>
      <p class="muted"></p>

      <h2>
        <span></span>
      </h2>

      <a>
        <h3></h3>
      </a>

      <table id="get_table">
        <tbody>
          <tr>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>

      <a>
        <h3></h3>
      </a>

      <table id="post_table">
        <tbody>
          <tr>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>

      <a>
        <h3></h3>
      </a>

      <table id="request_headers_table">
        <tbody>
          <tr>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>

      <a>
        <h3></h3>
      </a>

      <table id="cookie_table">
        <tbody>
          <tr>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>

      <h2>
        <span></span>
      </h2>

      <a>
        <h3></h3>
      </a>

      <table id="response_headers_table">
        <tbody>
          <tr>
            <td></td>
            <td></td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Config Values -->
    <div id="ci-config" class="tab">
      <h2></h2>
    </div>
  </div>
