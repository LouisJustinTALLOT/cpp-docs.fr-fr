---
title: Touches accélérateur (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: bb407538f254df5f187ff91b85a8eaa753a52287
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362385"
---
# <a name="accelerator-keys-c"></a>Touches accélérateur (C++)

## <a name="predefined-accelerator-keys"></a>Touches accélérateur prédéfinies

Il existe un certain nombre de touches d'accès rapide prédéfinies qui peuvent faire partie d'un projet d'application Windows. Certaines de ces touches virtuelles sont destinées à l'environnement Windows. D’autres prennent en charge les applications de navigateur ou Unicode. Vous pouvez utiliser ces touches en tant que touches d'accès rapide.

|Touche|Description|
|---------|-----------------|
|VK_ACCEPT|(IME) accepter|
|VK_BROWSER_BACK|(Windows) Navigateur, **retour** clé|
|VK_BROWSER_FAVORITES|(Windows) Navigateur, **favoris** clé|
|VK_BROWSER_FORWARD|(Windows) Navigateur, **transférer** clé|
|VK_BROWSER_HOME|(Windows) Navigateur, **Démarrer** et **accueil** clé|
|VK_BROWSER_REFRESH|(Windows) Navigateur, **Actualiser** clé|
|VK_BROWSER_SEARCH|(Windows) Navigateur, **recherche** clé|
|VK_BROWSER_STOP|(Windows) Navigateur, **arrêter** clé|
|VK_CONVERT|Conversion (IME)|
|VK_FINAL|Mode final IME)|
|VK_HANGUEL|(IME) Mode de Hanguel (conservé pour la compatibilité, utilisez le VK_HANGUL)|
|VK_HANGUL|(IME) Mode Hangul|
|VK_HANJA|(IME) Mode Hanja|
|VK_JUNJA|(IME) En mode Junja|
|VK_KANA|(IME) Mode de caractères Kana|
|VK_KANJI|(IME) Mode Kanji|
|VK_LAUNCH_APP1|(Windows) **Démarrer l’Application 1** clé|
|VK_LAUNCH_APP2|(Windows) **Démarrer l’Application 2** clé|
|VK_LAUNCH_MAIL|(Windows) **Démarrer messagerie** clé|
|VK_LAUNCH_MEDIA_SELECT|(Windows) **Sélectionner média** clé|
|VK_LCONTROL|**Ctrl de gauche** clé|
|VK_LMENU|**Menu de gauche** clé|
|VK_LSHIFT|**MAJ gauche** clé|
|VK_MEDIA_NEXT_TRACK|(Windows) **Piste suivante** clé|
|VK_MEDIA_PLAY_PAUSE|(Windows) **Lecture/Pause du média** clé|
|VK_MEDIA_PREV_TRACK|(Windows) **Piste précédente** clé|
|VK_MEDIA_STOP|(Windows) **Media arrêter** clé|
|VK_MODECHANGE|Demande de modification de mode IME)|
|VK_NONCONVERT|Non-conversion (IME)|
|VK_OEM_1|(Windows) Pour le clavier américain standard, le **; :** clé|
|VK_OEM_102|(Windows) La clé de chevron ou la touche de barre oblique inverse sur le RT de 102 touches|
|VK_OEM_2|(Windows) Pour le clavier américain standard, le **/ ?** clé|
|VK_OEM_3|(Windows) Pour le clavier américain standard, le **`~** clé|
|VK_OEM_4|(Windows) Pour le clavier américain standard, le **[{** clé|
|VK_OEM_5|(Windows) Pour le clavier américain standard, le **\\ &#124;** clé|
|VK_OEM_6|(Windows) Pour le clavier américain standard, le **]}** clé|
|VK_OEM_7|(Windows) Pour le clavier américain standard, la clé 'unique-devis/guillemet'|
|VK_OEM_COMMA|(Windows) Pour n’importe quel pays/région, le **,** clé|
|VK_OEM_MINUS|(Windows) Pour n’importe quel pays/région, le **-** clé|
|VK_OEM_PERIOD|(Windows) Pour n’importe quel pays/région, le **.** clé|
|VK_OEM_PLUS|(Windows) Pour n’importe quel pays/région, le **+** clé|
|VK_PACKET|(Windows) Utilisé pour passer des caractères Unicode comme s’ils sont des séquences de touches.|
|VK_RCONTROL|**Ctrl de droite** clé|
|VK_RMENU|**Menu de droite** clé|
|VK_RSHIFT|**MAJ droite** clé|
|VK_SLEEP|**Ordinateur en veille** clé|
|VK_VOLUME_DOWN|(Windows) **Baisser le volume** clé|
|VK_VOLUME_MUTE|(Windows) **Volume muet** clé|
|VK_VOLUME_UP|(Windows) **Monter le volume** clé|
|VK_XBUTTON1|(Windows) **X1** bouton de la souris|
|VK_XBUTTON2|(Windows) **X2** bouton de la souris|

## <a name="accelerator-key-association"></a>Association de clé d’accès rapide

Bien souvent, vous souhaitez qu'un élément de menu et une combinaison de touches du clavier permettent d'exécuter la même commande de programme. Vous effectuez cette action en attribuant le même identificateur de ressource (ID) à l’élément de menu et à une entrée dans la table d’accélérateurs de votre application. Vous modifiez ensuite la légende de l'élément de menu pour afficher le nom de l'accélérateur. Pour plus d’informations sur les éléments de menu et les touches d’accès rapide, consultez [commandes de Menu](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’accélérateurs](../windows/accelerator-editor.md)<br/>