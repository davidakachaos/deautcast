---
layout: single
title: Contact
lang: nl
---
Via onderstaande formulier kun je contact opnemen met de AutCast. Ik sta altijd open voor ideeën en mensen om mee te praten. Ook via de volgende plekken is de podcast bereikbaar:

- Via email: {{ "autcast@myautsiticself.nl" | create_mailto_link }}
- Via [LinkedIn](https://www.linkedin.com/in/myautisticself/)
- Via [Discord](https://discord.gg/5TEuS8xZSD)

Of uiteraard via het onderstaande formulier:


<form class="ui form" id="my-form"
  action="https://formspree.io/f/xknpvyvq"
  method="POST"
>
  <div class="field">
    <label>Naam:</label>
    <input type="text" name="name" placeholder="Uw naam" />
  </div>
  <div class="field">
    <label>Email adres:</label>
    <input type="email" name="email" placeholder="Uw email adres" />
  </div>
  <div class="field">
    <label>Bericht:</label>
    <textarea rows="5" name="message" placeholder="Uw bericht...">
    </textarea>
  </div>
  <div id="my-form-status" style="display: none;" class="ui message">
    <div class="header"></div>
    <p></p>
  </div>
  <input type="hidden" name="_subject" value="Nieuw bericht!" />
  <input type="hidden" name="_language" value="nl" />
  <input type="text" name="_gotcha" />
  <button class="ui button" id="my-form-button">Verstuur!</button>
  <p ></p>
</form>
<script type="text/javascript">
window.addEventListener("DOMContentLoaded", function() {

  // get the form elements defined in your form HTML above

  var form = document.getElementById("my-form");
  var button = document.getElementById("my-form-button");
  var status = document.getElementById("my-form-status");

  // Success and Error functions for after the form is submitted

  function success() {
    form.reset();
    button.style = "display: none ";
    // status.innerHTML = "Bedankt voor uw bericht!";
    $('#my-form-status').addClass('success');
    $('#my-form-status div.header').text('Bedankt!');
    $('#my-form-status p').text('Bedankt voor uw bericht!');
    $('#my-form-status').show();

  }

  function error() {
    // status.innerHTML = "Oops! Er was een probleem bij het versturen.";
    $('#my-form-status').addClass('error');
    $('#my-form-status div.header').text('Helaas!');
    $('#my-form-status p').text('Er was een probleem bij het versturen van uw bericht!');
    $('#my-form-status').show();
  }

  // handle the form submission event

  form.addEventListener("submit", function(ev) {
    ev.preventDefault();
    $('my-form').addClass('loading');
    var data = new FormData(form);
    ajax(form.method, form.action, data, success, error);
  });
});

// helper function for sending an AJAX request

function ajax(method, url, data, success, error) {
  var xhr = new XMLHttpRequest();
  xhr.open(method, url);
  xhr.setRequestHeader("Accept", "application/json");
  xhr.onreadystatechange = function() {
    if (xhr.readyState !== XMLHttpRequest.DONE) return;
    if (xhr.status === 200) {
      success(xhr.response, xhr.responseType);
      $('my-form').removeClass('loading');
    } else {
      error(xhr.status, xhr.response, xhr.responseType);
      $('my-form').removeClass('loading');
    }
  };
  xhr.send(data);
}

</script>
