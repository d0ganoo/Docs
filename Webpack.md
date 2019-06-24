

# Webpack

 Qualifié de “bundler”, il vous permettra de faire bien des choses : utiliser un serveur local, utiliser le Live Reload, mais aussi et surtout compiler tous vos fichiers pour les regrouper en un seul.


## Live reload vs hot reload

#### Live reload

Le live reload recharge/rafraîchit l'intégralité de l'application lorsqu'un fichier est modifié. Par exemple, si vous faites des changements dans la navigation et que vous sauvegardé ses changements, le live reload reclancera l'application et la chargera depuis la route initial.

#### Hot reload

Le hot reload rafraîchit uniquement les fichiers qui ont été modifiés sans perdre l'état de l'application. Par exemple, si vous faites des modifications de style, l'état de l'application ne changera pas mais les nouveaux styles vont apparaitre sur la page. Pas de retour à la première page de l'application
