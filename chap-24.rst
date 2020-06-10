Exercice d’application – version 13
===================================

La version 13 amène peu de changements : elle sécurise l’accès aux
fichiers de l’application.

Avec la version 12, on peut demander l’URL suivante
**[http://localhost/php7/scripts-web/impots/version-12/config.json]**.
On obtient alors la page suivante (Firefox) :

|image0|

Or ce fichier **[config.json]** contient des informations sensibles tels
les identifiants des utilisateurs autorisés à utiliser l’application. Il
ne faut pas qu’il soit accessible aux utilisateurs. Il en est de même
pour tous les fichiers de l’application à l’exception des fichiers
**[main.php, index.php, Views/logo.jpg]** qui eux doivent être
accessibles de l’extérieur. En effet les vues ont besoin d’avoir un
accès HTTP au logo de l’application. La version 13 amène une solution
simple à ce problème.

Dans Netbeans, nous faisons un copier-coller du dossier **[version-12]**
dans **[version-13]** :

|image1|

-  en **[1]**, dans le dossier racine de l’application, nous ne laissons
   que les scripts **[index.php, main.php]** ;

-  en **[2]**, les fichiers de configuration sont placés dans un dossier
   **[Config]** ;

-  en **[3]**, l’image **[logo.jpg]** est placée dans un dossier
   **[Resources]** ;

Le serveur HTTP utilisé est ici un serveur Apache. Celui-ci permet de
contrôler l’accès à un dossier via un fichier **[.htaccess]**. Dans tous
les dossiers auxquels nous voulons interdire un accès direct par URL,
nous créons le fichier **[.htaccess]** suivant :

|image2|

Ces deux lignes font que tout accès au dossier est interdit à tous.

Nous plaçons ce fichier dans tous les dossiers de l’application sauf
dans le dossier racine et le dossier **[Resources]**. Finalement seuls
trois fichiers sont accessibles de l’extérieur : **[index.php, main.php,
Resources/logo.jpg]**.

Faisons quelques essais :

|image3|

|image4|

|image5|

|image6|

|image7|

Quelques modifications doivent être faites dans le code :

Dans le fichier **[Config/config.json]** :

|image8|

Dans le fichier **[main.php]** :

|image9|

Dans le fichier **[Views/v-bandeau.php]** :

|image10|

.. |image0| image:: ./chap-24/media/image1.png
   :width: 5.0752in
   :height: 3.48819in
.. |image1| image:: ./chap-24/media/image2.png
   :width: 2.72835in
   :height: 2.5in
.. |image2| image:: ./chap-24/media/image3.png
   :width: 1.7126in
   :height: 0.82717in
.. |image3| image:: ./chap-24/media/image4.png
   :width: 4.45709in
   :height: 1.24803in
.. |image4| image:: ./chap-24/media/image5.png
   :width: 4.50433in
   :height: 1.20472in
.. |image5| image:: ./chap-24/media/image6.png
   :width: 3.95275in
   :height: 1.55157in
.. |image6| image:: ./chap-24/media/image7.png
   :width: 6.14567in
   :height: 1.22835in
.. |image7| image:: ./chap-24/media/image8.png
   :width: 6.01614in
   :height: 3.94527in
.. |image8| image:: ./chap-24/media/image9.png
   :width: 4.79173in
   :height: 1.0752in
.. |image9| image:: ./chap-24/media/image10.png
   :width: 3.09843in
   :height: 0.93346in
.. |image10| image:: ./chap-24/media/image11.png
   :width: 4.24016in
   :height: 1.57835in
