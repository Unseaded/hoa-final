---
layout: page
title: Contact Us
---

We'd love to hear from you. For general inquiries, architectural requests, or to report a concern, please use the form below.

### Mailing Address & Management

{{ site.data.settings.management_info | markdownify }}

<div class="divider">{% include svg-fence.html %}</div>

### Send a Message

<!-- Note: Replace the 'action' URL with your Formspree form ID once created -->
<form action="https://formspree.io/f/your_formspree_id" method="POST">
  <label for="name">Name</label>
  <input type="text" id="name" name="name" required>
  
  <label for="email">Email Address</label>
  <input type="email" id="email" name="email" required>
  
  <label for="message">Message</label>
  <textarea id="message" name="message" rows="5" required></textarea>
  
  <button type="submit">Send Message</button>
</form>

<p><small>Having trouble with the form? Email the board directly at <a href="mailto:{{ site.email }}">{{ site.email }}</a>.</small></p>
