---
title: Les touches accélérateur prédéfinies | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts, predefined
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa5b42fc846f3b4f21dc8045e67d8ebc347601ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880793"
---
# <a name="predefined-accelerator-keys"></a>Touches accélérateur prédéfinies
Il existe un certain nombre de touches d'accès rapide prédéfinies qui peuvent faire partie d'un projet d'application Windows. Certaines de ces touches virtuelles sont destinées à l'environnement Windows. D'autres sont destinées aux navigateurs ou aux applications Unicode. Vous pouvez utiliser ces touches en tant que touches d'accès rapide.  
  
|Touche|Description|  
|---------|-----------------|  
|VK_ACCEPT|Acceptation IME|  
|VK_BROWSER_BACK|Windows : touche de page précédente du navigateur|  
|VK_BROWSER_FAVORITES|Windows : touche des Favoris du navigateur|  
|VK_BROWSER_FORWARD|Windows : touche de page suivante du navigateur|  
|VK_BROWSER_HOME|Windows : touche de page d'accueil du navigateur|  
|VK_BROWSER_REFRESH|Windows : touche d'actualisation du navigateur|  
|VK_BROWSER_SEARCH|Windows : touche de recherche du navigateur|  
|VK_BROWSER_STOP|Windows : touche d'arrêt du navigateur|  
|VK_CONVERT|Conversion IME|  
|VK_FINAL|Mode final IME|  
|VK_HANGUEL|Mode IME Hanguel (conservé pour des raisons de compatibilité ; utilisez VK_HANGUL)|  
|VK_HANGUL|Mode IME Hangul|  
|VK_HANJA|Mode IME Hanja|  
|VK_JUNJA|Mode IME Junja|  
|VK_KANA|Mode IME Kana|  
|VK_KANJI|Mode IME Kanji|  
|VK_LAUNCH_APP1|Windows : touche de démarrage d'application 1|  
|VK_LAUNCH_APP2|Windows : touche de démarrage d'application 2|  
|VK_LAUNCH_MAIL|Windows : touche de démarrage de la messagerie|  
|VK_LAUNCH_MEDIA_SELECT|Windows : touche de sélection du média|  
|VK_LCONTROL|Touche Control gauche|  
|VK_LMENU|Touche Menu gauche|  
|VK_LSHIFT|Touche Maj gauche|  
|VK_MEDIA_NEXT_TRACK|Windows : touche de piste suivante|  
|VK_MEDIA_PLAY_PAUSE|Windows : touche de lecture/pause du média|  
|VK_MEDIA_PREV_TRACK|Windows : touche de piste précédente|  
|VK_MEDIA_STOP|Windows : touche d'arrêt du média|  
|VK_MODECHANGE|Requête de changement de mode IME|  
|VK_NONCONVERT|Non-conversion IME|  
|VK_OEM_1|Windows : pour le clavier standard américain, touche ';:'|  
|VK_OEM_102|Windows : soit la touche du crochet gauche, soit la touche de barre oblique inverse sur le clavier RT de 102 touches|  
|VK_OEM_2|Windows : pour le clavier américain standard, le '/ ?' clé|  
|VK_OEM_3|Windows : pour le clavier américain standard, touche '`~'|  
|VK_OEM_4|Windows : pour le clavier américain standard, touche '[{'|  
|VK_OEM_5|Windows : pour le clavier américain standard, le «\\&#124;' clé|  
|VK_OEM_6|Windows : pour le clavier américain standard, touche ']}'|  
|VK_OEM_7|Windows : pour le clavier américain standard, touche 'apostrophe/guillemet'|  
|VK_OEM_COMMA|Windows : pour l'ensemble des pays/régions, touche ','|  
|VK_OEM_MINUS|Windows : pour l'ensemble des pays/régions, touche '-'|  
|VK_OEM_PERIOD|Windows : pour l'ensemble des pays/régions, touche '.'|  
|VK_OEM_PLUS|Windows : pour l'ensemble des pays/régions, touche '+'|  
|VK_PACKET|Windows : sert à passer des caractères Unicode comme s'il s'agissait de séquences de touches.|  
|VK_RCONTROL|Touche Control droite|  
|VK_RMENU|Touche Menu droite|  
|VK_RSHIFT|Touche Maj droite|  
|VK_SLEEP|Touche de veille|  
|VK_VOLUME_DOWN|Windows : touche de réduction du volume|  
|VK_VOLUME_MUTE|Windows : touche de désactivation du volume|  
|VK_VOLUME_UP|Windows : touche d'augmentation du volume|  
|VK_XBUTTON1|Windows : bouton de souris X1|  
|VK_XBUTTON2|Windows : bouton de souris X2|  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.*  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur d’accélérateurs](../windows/accelerator-editor.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)