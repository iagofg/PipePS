# PipePS

## A flexible customizable minimalistic CMS with onsite content editor

```html
     <!DOCTYPE html>
     <html>
       <body>
         <header class="text-end">{{login panel}}<hr></header>
         <main>
           <section class="col-sm-4">{{editable section_1}}</section>
           <section class="col-sm-4">{{editable section_2}}</section>
           <section class="col-sm-4">{{editable section_3}}</section>
         </main>
       </body>
     </html>
```
Example of default.html in the tpl/ folder. If not other mode like a non automatic or library is specified with $GLOBALS['pipeps-mode'] before including pipeps.min.php, then the actions of the **programmable main/default sequence in the topmost configuration section will be executed** (init, checkbefore, etcfind, etcrun, i18n, doactions, tplfind, include and checkafter) resulting in rendering the corresponding {{...}} template, for example default.html like shown.

You can name editable sections with any tag, placing an {{editable ...}} tag will be replaced with the section contents or, if you login with a user allowed to edit, an edit tag will appear:

![image](https://github.com/user-attachments/assets/36cfbf98-78a8-4a39-9fff-4b4c744a259c)

And if you click it an edit box will popup:

![image](https://github.com/user-attachments/assets/1033a3bc-cd98-495d-9e7b-5090a3930c36)

By default PipePS will store editable sections contents as html files in the site/usr-CODE/edit/ folder where are loadable by webservices or by the CMS itself.

## HOW-TO manual setup (step-by-step)
1. **copy pipeps.min.php** into webserver, create index.php with: <?php include("../path/to/pipeps.min.php");
2. **open the index.php** with your browser: should see a blank page: pipeps.log WILL BE CREATED somewhere.
3. **locate pipeps.log**: it should be on /var/log or /tmp or C:\Windows\Temp or maybe in sys_get_temp_dir() folder ...or near index.php (this lastone alternative is NOT RECOMMENDED and you should AVOID it)
4. **create your site folder**: localhost/ or domain.com/ or 12.34.56.78/ (whatever used in browser, check log)
5. inside place etc/ folder, empty index.html, a **config named like AB12-CD34-EF45.php** with your own named-code
6. next to etc/ folder another **folder named usr-AB12-CD34-EF45/** (use same own code used for config file)
7. inside usr-.../ **create another folder named tpl/** with the **example default.html file** in the intro
8. **reload your browser**, you should see now the interpreted html template instead of a blank page
9. next to tpl/ **create the empty folders edit/ sessions/ and users/ and then create inside a YOUR_USER_NAME.user** file replacing values, with the following contents: &user=YOUR_USER_NAME&hash=PASSWORD_MD5_HASH&perm.edit=1&
