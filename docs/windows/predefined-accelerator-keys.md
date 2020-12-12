---
description: 'En savoir plus sur : touches accélérateur (C++)'
title: Touches accélérateur (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 397e0735ba33af6adf8f10c6188f73d6f504e68b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180095"
---
# <a name="accelerator-keys-c"></a>Touches accélérateur (C++)

## <a name="predefined-accelerator-keys"></a>Touches accélérateur prédéfinies

Il existe un certain nombre de touches d'accès rapide prédéfinies qui peuvent faire partie d'un projet d'application Windows. Certaines de ces touches virtuelles sont destinées à l'environnement Windows. D’autres prennent en charge les applications de navigateur ou Unicode. Vous pouvez utiliser ces touches en tant que touches d'accès rapide.

|Clé|Description|
|---------|-----------------|
|VK_ACCEPT|(IME) accepter|
|VK_BROWSER_BACK|Windows Navigateur, touche **précédent**|
|VK_BROWSER_FAVORITES|Windows Navigateur, touche **favoris**|
|VK_BROWSER_FORWARD|Windows Navigateur, touche de **direction**|
|VK_BROWSER_HOME|Windows Navigateur, clé de **démarrage** et d' **Accueil**|
|VK_BROWSER_REFRESH|Windows Navigateur, **Actualiser** la clé|
|VK_BROWSER_SEARCH|Windows Navigateur, touche de **recherche**|
|VK_BROWSER_STOP|Windows Navigateur, touche **arrêter**|
|VK_CONVERT|(IME) Convert|
|VK_FINAL|(IME) mode final|
|VK_HANGUEL|DICAUX Mode Hangul (conservé pour la compatibilité, utilisez VK_HANGUL)|
|VK_HANGUL|DICAUX Mode Hangul|
|VK_HANJA|DICAUX Mode hanja|
|VK_JUNJA|DICAUX Mode Junja|
|VK_KANA|DICAUX Mode Kana|
|VK_KANJI|DICAUX Mode kanji|
|VK_LAUNCH_APP1|Windows Démarrer la clé de l' **application 1**|
|VK_LAUNCH_APP2|Windows Démarrer la clé de l' **application 2**|
|VK_LAUNCH_MAIL|Windows **Démarrer** la clé de messagerie|
|VK_LAUNCH_MEDIA_SELECT|Windows **Sélectionner** une clé de support|
|VK_LCONTROL|Touche **CTRL de gauche**|
|VK_LMENU|Touche du **menu de gauche**|
|VK_LSHIFT|Touche **MAJ de gauche**|
|VK_MEDIA_NEXT_TRACK|Windows Touche **piste suivante**|
|VK_MEDIA_PLAY_PAUSE|Windows Touche **lecture/pause du média**|
|VK_MEDIA_PREV_TRACK|Windows Touche **piste précédente**|
|VK_MEDIA_STOP|Windows Touche **arrêter le média**|
|VK_MODECHANGE|(IME) mode de demande de modification|
|VK_NONCONVERT|(IME) non converti|
|VK_OEM_1|Windows Pour le clavier américain standard, la touche **;:**|
|VK_OEM_102|Windows La touche de crochet angulaire ou la touche de barre oblique inverse sur le clavier RT 102-Key|
|VK_OEM_2|Windows Pour le clavier américain standard, le **/ ?** key|
|VK_OEM_3|Windows Pour le clavier américain standard, la **`~** clé|
|VK_OEM_4|Windows Pour le clavier américain standard, la **[{** Key|
|VK_OEM_5|Windows Pour le clavier américain standard, la touche **\\&#124;**|
|VK_OEM_6|Windows Pour le clavier standard américain, la touche **]}**|
|VK_OEM_7|Windows Pour le clavier standard américain, la touche « apostrophe/guillemet »|
|VK_OEM_COMMA|Windows Pour n’importe quel pays/région, la touche **,**|
|VK_OEM_MINUS|Windows Pour n’importe quel pays/région, la **-** clé|
|VK_OEM_PERIOD|Windows Pour n’importe quel pays/région, le **.** key|
|VK_OEM_PLUS|Windows Pour n’importe quel pays/région, la **+** clé|
|VK_PACKET|Windows Utilisé pour passer des caractères Unicode comme s’il s’agissait de séquences de touches.|
|VK_RCONTROL|Touche **CTRL de droite**|
|VK_RMENU|Touche de **menu de droite**|
|VK_RSHIFT|Touche **MAJ droite**|
|VK_SLEEP|Touche de mise en veille de l' **ordinateur**|
|VK_VOLUME_DOWN|Windows **Réduire la** clé du volume|
|VK_VOLUME_MUTE|Windows Touche **volume muet**|
|VK_VOLUME_UP|Windows Touche **monter le volume**|
|VK_XBUTTON1|Windows **X1** bouton de la souris|
|VK_XBUTTON2|Windows Bouton **x2** de la souris|

## <a name="accelerator-key-association"></a>Association de touches accélérateur

Bien souvent, vous souhaitez qu'un élément de menu et une combinaison de touches du clavier permettent d'exécuter la même commande de programme. Vous pouvez effectuer cette action en affectant le même identificateur de ressource (ID) à l’élément de menu et à une entrée dans la table d’accélérateurs de votre application. Vous modifiez ensuite la légende de l'élément de menu pour afficher le nom de l'accélérateur. Pour plus d’informations sur les éléments de menu et les touches d’accès rapide, consultez [commandes de menu](./menu-command-properties.md).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’accélérateurs](../windows/accelerator-editor.md)<br/>
