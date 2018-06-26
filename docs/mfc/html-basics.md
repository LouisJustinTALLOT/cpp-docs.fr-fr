---
title: Principes de base HTML | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c4ebbc8e792e36461f7c52c17fa23815239e323
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929088"
---
# <a name="html-basics"></a>Éléments fondamentaux relatifs à HTML
La plupart des navigateurs ont la capacité d'examiner la source HTML des pages que vous consultez. Lorsque vous affichez la source, vous pouvez voir plusieurs balises HTML (HyperText Markup Language) entourées de crochets pointus (<>) et entrecoupées avec du texte.  
  
 Les étapes ci-dessous utilisent les balises HTML pour générer une page Web. Dans ces étapes, vous saisirez le texte en clair dans un fichier grâce au Bloc-notes, vous apporterez des modifications, enregistrerez le fichier, puis rechargerez la page du navigateur pour afficher vos modifications.  
  
#### <a name="to-create-an-html-file"></a>Pour créer un fichier HTML  
  
1.  Ouvrez le Bloc-notes ou un éditeur de texte brut.  
  
2.  À partir de la **fichier** menu, choisissez **nouveau**.  
  
3.  Tapez les lignes suivantes :  
  
 ```  
 <HTML>  
 <HEAD>  
 <TITLE>Top HTML Tags</TITLE>  
 </HEAD>  
 </HTML>  
 ```  
  
4.  À partir de la **fichier** menu, choisissez **enregistrer**, enregistrez le fichier sous c:\webpages\First.htm. Laissez le fichier ouvert dans l'éditeur.  
  
5.  Commutateur vers votre navigateur et de la **fichier** menu, choisissez **ouvrir**, ou de type *file://C:/webpages/first.htm* dans la zone d’édition URL du navigateur. Vous devez voir une page vide avec la légende de fenêtre "Étiquettes HTML principales"  
  
     Notez que les balises sont affichées par paires et incluses entre crochets pointus. Les étiquettes ne respectent pas la casse, mais la mise en majuscules est souvent utilisée pour distinguer les étiquettes.  
  
     La balise \<HTML > démarre le document et la balise \</HTML > le termine. Les étiquettes de fin (pas toujours requises) sont les mêmes que les étiquettes de début à la seule différence qu’une barre oblique (/) précède l’étiquette. Il ne doit y avoir aucun espace entre le crochet pointu (<) et le début de l’étiquette.  
  
6.  Commutateur au bloc-notes et après le \</head > de la ligne, tapez :  
  
 ```  
 <BODY>  
    HTML is swell.  
    Life is good.  
 </BODY>  
 ```  
  
7.  À partir de la **fichier** menu, choisissez **enregistrer**.  
  
8.  Basculez vers votre navigateur et actualisez la page.  
  
     Les mots apparaissent dans la zone cliente de votre fenêtre de navigateur. Notez que votre retour chariot est ignoré. Si vous souhaitez avoir un saut de ligne, vous devez inclure une balise `<BR>` après la première ligne.  
  
     Pour toutes les étapes qui suivent, insérez le texte n’importe où entre \<corps > et \</BODY > pour ajouter le corps de votre document.  
  
9. Ajoutez un en-tête :  
  
 ```  
 <H3>Here's the big picture</H3>  
 ```  
  
10. Ajoutez une image, en utilisant un fichier .gif enregistré dans le même répertoire que votre page :  
  
 ```  
 <IMG src="yourfile.gif">  
 ```  
  
11. Ajoutez une liste :  
  
 ```  
 <UL>Make me an unordered list.  
 <LI>One programmer</LI>  
 <LI>Ten SDKs</LI>  
 <LI>Great Internet Apps</LI>  
 </UL>  
 ```  
  
12. Pour numéroter la liste au lieu de cela, utilisez associés \<OL > et \</OL > balises à la place de la \<UL > et \</UL > balises.  
  
 Cela peut vous aider à démarrer. Si vous consultez une fonctionnalité intéressante sur une page web, déterminez comment elle a été créée en examinant la source HTML. Les éditeurs HTML tels que Microsoft Front Page peuvent être utilisés pour créer des pages simples et avancées.  
  
 Voici la source HTML complète pour le fichier que vous aviez créé :  
  
```  
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
  
 [http://www.w3.org/pub/WWW/MarkUp/](http://www.w3.org/pub/www/markup/)  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

