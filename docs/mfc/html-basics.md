---
title: Éléments fondamentaux relatifs à HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 29ca2e3df4981db22a10281ba2a2938fc91d5b46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619999"
---
# <a name="html-basics"></a>Éléments fondamentaux relatifs à HTML

La plupart des navigateurs ont la capacité d'examiner la source HTML des pages que vous consultez. Lorsque vous affichez la source, vous pouvez voir plusieurs balises HTML (Hypertext Markup Language), entourées de crochets pointus (<>), intercalés avec du texte.

Les étapes ci-dessous utilisent les balises HTML pour générer une page Web. Dans ces étapes, vous saisirez le texte en clair dans un fichier grâce au Bloc-notes, vous apporterez des modifications, enregistrerez le fichier, puis rechargerez la page du navigateur pour afficher vos modifications.

#### <a name="to-create-an-html-file"></a>Pour créer un fichier HTML

1. Ouvrez le Bloc-notes ou un éditeur de texte brut.

1. Dans le menu **fichier** , choisissez **nouveau**.

1. Tapez les lignes suivantes :

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. Dans le menu **fichier** , choisissez **Enregistrer**, puis enregistrez le fichier en tant que c:\webpages\First.htm. Laissez le fichier ouvert dans l'éditeur.

1. Basculez vers votre navigateur et, dans le menu **fichier** , choisissez **ouvrir**, ou tapez *file://C:/webpages/First.htm* dans la zone d’édition URL du navigateur. Vous devez voir une page vide avec la légende de fenêtre "Balises HTML principales"

   Notez que les étiquettes sont affichées par paires et incluses entre crochets pointus. Les étiquettes ne respectent pas la casse, mais la mise en majuscules est souvent utilisée pour distinguer les étiquettes.

   La balise \<HTML> démarre le document, et la balise la \</HTML> termine. Les balises de fin (pas toujours requises) sont les mêmes que les balises de début à la seule différence qu'une barre oblique (/) précède la balise. Il ne doit y avoir aucun espace entre le Chevron (<) et le début de la balise.

1. Revenez au bloc-notes et, après la \</HEAD> ligne, tapez :

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. Dans le menu **fichier** , choisissez **Enregistrer**.

1. Basculez vers votre navigateur et actualisez la page.

   Les mots apparaissent dans la zone cliente de votre fenêtre de navigateur. Notez que votre retour chariot est ignoré. Si vous souhaitez avoir un saut de ligne, vous devez inclure une balise `<BR>` après la première ligne.

   Pour toutes les étapes qui suivent, insérez le texte n’importe où entre \<BODY> et \</BODY> pour ajouter le corps de votre document.

1. Ajoutez un en-tête :

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Ajoutez une image, en utilisant un fichier .gif enregistré dans le même répertoire que votre page :

    ```html
    <IMG src="yourfile.gif">
    ```

1. Ajoutez une liste :

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Pour numéroter la liste à la place, utilisez des \<OL> \</OL> balises et paires à la place des \<UL> \</UL> balises et.

Cela peut vous aider à démarrer. Si vous consultez une fonctionnalité intéressante sur une page web, déterminez comment elle a été créée en examinant la source HTML. Les éditeurs HTML tels que Microsoft Front Page peuvent être utilisés pour créer des pages simples et avancées.

Voici la source HTML complète pour le fichier que vous aviez créé :

```html
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

Pour une description complète des étiquettes, attributs et extensions, consultez la spécification du langage HTML (Hypertext Markup Language) :

[Dernière version publiée du code html](https://www.w3.org/TR/html/) sur W3C.org.

## <a name="see-also"></a>Voir aussi

[Concepts de base de la programmation Internet MFC](mfc-internet-programming-basics.md)
