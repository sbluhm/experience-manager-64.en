---
title: Considerations when running AdministrationConsole
seo-title: Considerations when running AdministrationConsole
description: This document lists a few points to consider when running Administration Console.
seo-description: This document lists a few points to consider when running Administration Console.
uuid: 482cc976-e0df-4f32-b9fa-c0283559776d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8183370d-dba2-4c42-b217-49b54bf4db0d
index: y
internal: n
snippet: y
---

# Considerations when running AdministrationConsole{#considerations-when-running-administrationconsole}

These are some things to consider when running Administration Console:

* If you access administration console using the URL http://*[hostname]*:*[port]*/adminui, the specified host name cannot contain underscore characters. Otherwise, links to some areas of the administration console may not work properly.
* If you run administration console in Windows Explorer on a Japanese OS, you may encouter these problems:

    * Clicking a link returns you to the login page instead of to the expected link.
    * Clicking a link displays a permission error.

  Best practice is run administration console from another browser, such as Mozilla Firefox, to ensure that no links will fail.

* Do not use backslash characters () when performing searches in administration console.
