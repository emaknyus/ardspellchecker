Indonesian Spellchecker
=======================
An Indonesian spellchecker as a jquery plugins. Suitable for any online html (WYSWYG) editor.

Installation:
============
`pip install -r requirements.txt`

Run `speller.py`. 
The default port for flask is `5000`

Usage:
======
Add this snippets to your html page:
`<link rel="stylesheet" href="http://host_or_domain:port/static/css/spellcheck.css" />`
`<script type="text/javascript" src="http://host_or_domain:port/static/js/spellcheck.js" />`

And then in your bottom page, before `</body>` tag, add this lines:
```
<script type="text/javascript">
    (function() {

      // Init the html spellchecker
      var spellchecker = new $.SpellChecker('#the_id_for_editable_content', {
        parser: 'html',
        webservice: {
          path: 'http://host_or_domain:port/',
        },
        suggestBox: {
          position: 'below'
        },
        local: {
          ignoreWord: 'Ignore word',
          ignoreAll: 'Ignore all',
          ignoreForever: 'Add to dictionary'
        }
      });

      // Bind spellchecker handler functions
      spellchecker.on('check.success', function() {
        alert('There are no incorrectly spelt words!');
      });
      var $button= $('<input/>').attr({ type: 'button', name:'spellcheck', id:'check-textarea', class:'check-textarea', value:'Check Spelling'});
      $('body').append($button);

      // Check the spelling
      $("#check-textarea").click(function(e){
        spellchecker.check();
      });

    })();
</script>
```



Powered By:
===========
ardwort
=======