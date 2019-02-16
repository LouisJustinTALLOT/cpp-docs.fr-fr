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
ms.openlocfilehash: 6ef8f84564d6fd1957452971cb1e88dc99aa27e9
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320508"
---
# <a name="accelerator-keys-c"></a>Touches accélérateur (C++)

## <a name="predefined-accelerator-keys"></a>Touches accélérateur prédéfinies

Il existe un certain nombre de touches d'accès rapide prédéfinies qui peuvent faire partie d'un projet d'application Windows. Certaines de ces touches virtuelles sont destinées à l'environnement Windows. D'autres sont destinées aux navigateurs ou aux applications Unicode. Vous pouvez utiliser ces touches en tant que touches d'accès rapide.

|Touche|Description|
|---------|-----------------|
|VK_ACCEPT|Acceptation IME|
|VK_BROWSER_BACK|Windows : Touche précédent du navigateur|
|VK_BROWSER_FAVORITES|Windows : Touche Favoris du navigateur|
|VK_BROWSER_FORWARD|Windows : Touche suivant du navigateur|
|VK_BROWSER_HOME|Windows : Clé d’accueil du navigateur|
|VK_BROWSER_REFRESH|Windows : Touche Actualiser du navigateur|
|VK_BROWSER_SEARCH|Windows : Touche Rechercher du navigateur|
|VK_BROWSER_STOP|Windows : Touche Arrêter du navigateur|
|VK_CONVERT|Conversion IME|
|VK_FINAL|Mode final IME|
|VK_HANGUEL|Mode IME Hanguel (conservé pour des raisons de compatibilité ; utilisez VK_HANGUL)|
|VK_HANGUL|Mode IME Hangul|
|VK_HANJA|Mode IME Hanja|
|VK_JUNJA|Mode IME Junja|
|VK_KANA|Mode IME Kana|
|VK_KANJI|Mode IME Kanji|
|VK_LAUNCH_APP1|Windows : Touche Démarrer l’Application 1|
|VK_LAUNCH_APP2|Windows : Touche Démarrer l’Application 2|
|VK_LAUNCH_MAIL|Windows : Touche de début de la messagerie|
|VK_LAUNCH_MEDIA_SELECT|Windows : Touche Sélectionner média|
|VK_LCONTROL|Touche Control gauche|
|VK_LMENU|Touche Menu gauche|
|VK_LSHIFT|Touche Maj gauche|
|VK_MEDIA_NEXT_TRACK|Windows : Touche de piste suivante|
|VK_MEDIA_PLAY_PAUSE|Windows : Touche Lecture/Pause du média|
|VK_MEDIA_PREV_TRACK|Windows : Touche de piste précédente|
|VK_MEDIA_STOP|Windows : Arrêter la clé de média|
|VK_MODECHANGE|Requête de changement de mode IME|
|VK_NONCONVERT|Non-conversion IME|
|VK_OEM_1|Windows : Pour le clavier américain standard, le « ; : « clé|
|VK_OEM_102|Windows : La clé de chevron ou la touche de barre oblique inverse sur le RT de 102 touches|
|VK_OEM_2|Windows : Pour le clavier américain standard, le « / » ? clé|
|VK_OEM_3|Windows : Pour le clavier américain standard, le '' ~' clé|
|VK_OEM_4|Windows : Pour le clavier américain standard, le ' [{' clé|
|VK_OEM_5|Windows : Pour le clavier américain standard, le «\\&#124;' clé|
|VK_OEM_6|Windows : Pour le clavier américain standard, le ']}' clé|
|VK_OEM_7|Windows : Pour le clavier américain standard, la clé 'unique-devis/guillemet'|
|VK_OEM_COMMA|Windows : Pour n’importe quel pays/région, la clé ''|
|VK_OEM_MINUS|Windows : Pour n’importe quel pays/région, le '-' clé|
|VK_OEM_PERIOD|Windows : Pour n’importe quel pays/région, le '.' clé|
|VK_OEM_PLUS|Windows : Pour n’importe quel pays/région, la touche '+'|
|VK_PACKET|Windows : Utilisé pour passer des caractères Unicode comme s’ils étaient des séquences de touches.|
|VK_RCONTROL|Touche Control droite|
|VK_RMENU|Touche Menu droite|
|VK_RSHIFT|Touche Maj droite|
|VK_SLEEP|Touche de veille|
|VK_VOLUME_DOWN|Windows : Touche baisser le volume|
|VK_VOLUME_MUTE|Windows : Touche Volume muet|
|VK_VOLUME_UP|Windows : Touche Monter le volume|
|VK_XBUTTON1|Windows : Bouton de souris x1|
|VK_XBUTTON2|Windows : Bouton de souris x2|

## <a name="accelerator-key-association"></a>Association de clé d’accès rapide

Bien souvent, vous souhaitez qu'un élément de menu et une combinaison de touches du clavier permettent d'exécuter la même commande de programme. Pour ce faire, vous assignez le même identificateur (ID) de ressource à l'élément de menu et à une entrée de la table d'accélérateurs de votre application. Vous modifiez ensuite la légende de l'élément de menu pour afficher le nom de l'accélérateur. Pour plus d’informations sur les éléments de menu et les touches d’accès rapide, consultez [association d’un élément de Menu à une touche accélérateur](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’accélérateurs](../windows/accelerator-editor.md)<br/>