---
title: "Prise en charge des jeux de caractères multioctets (MBCS) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6c7bd1477f62e9c78b5e71dfe3723e804283d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Prise en charge des jeux de caractères multioctets (MBCS)
Les jeux de caractères multioctets (MBSC) sont une approche plus ancienne de la nécessité de prendre en charge certains jeux de caractères (japonais et chinois, par exemple) qui ne peuvent pas être représentés par un seul octet. Si vous procédez à un nouveau développement, vous devez utiliser Unicode pour toutes les chaînes de texte à l'exception peut-être des chaînes système qui ne sont pas visibles des utilisateurs finaux. MBCS est une technologie héritée qui n'est pas recommandée pour un nouveau développement.  
  
 L'implémentation MBCS la plus courante repose sur les jeux caractères codés sur deux octets (DBCS). Visual C++ en général, et MFC en particulier, est totalement compatible avec DBCS.  
  
 Pour obtenir des exemples, consultez les fichiers de code source MFC.  
  
 Pour les plateformes utilisées sur les marchés dont les langues utilisent des jeux de caractères volumineux, la meilleure alternative au format Unicode est MBCS. MFC prend en charge MBCS en utilisant des types de données internationalisables et des fonctions runtime C. Vous devez en faire de même dans votre code.  
  
 Dans le cadre de MBCS, les caractères sont codés sur 1 ou 2 octets. Dans les caractères codés sur 2 octets, le premier octet (ou octet de tête) signale que lui-même et l'octet suivant doivent être interprétés comme un seul et même caractère. Le premier octet est issu d'une plage de codes réservée à une utilisation comme octets de tête. La possibilité que les plages d'octets puissent ou non être des octets de tête dépend de la page de codes utilisée. Par exemple, la page de codes japonaise 932 utilise la plage de 0x81 à 0x9F en tant qu'octets de tête, alors que la page de codes coréenne 949 utilise une plage différente.  
  
 Prenez en compte tous les éléments suivants dans votre programmation MBCS.  
  
 Caractères MBCS dans l'environnement  
 Les caractères MBCS peuvent apparaître dans des chaînes telles que des noms de fichiers et de répertoires.  
  
 Opérations de modification  
 Les opérations de modification dans les applications MBCS doivent porter sur des caractères, et non des octets. Le caret ne doit pas fractionner un caractère, la touche DROITE doit déplacer le curseur d'un caractère vers la droite, et ainsi de suite. **Supprimer** doit supprimer un caractère ; **Annuler** doit le réinsérer.  
  
 Gestion des chaînes  
 Dans une application qui utilise MBCS, la gestion des chaînes pose des problèmes spécifiques. Les caractères des deux largeurs étant mélangés dans une même chaîne, vous devez penser à vérifier la présence d'octets de tête.  
  
 Prise en charge de la bibliothèque Runtime  
 La bibliothèque Runtime C et MFC prennent en charge la programmation sur un octet, MBCS et Unicode. Les chaînes sur un octet sont traitées avec la `str` famille de fonctions d’exécution, les chaînes MBCS sont traitées avec correspondant `_mbs` les fonctions et les chaînes Unicode sont traités avec correspondant *wcs* fonctions. Les implémentations des fonctions membres de la classe MFC utilisent des fonctions runtime portables qui sont mappées, quand les circonstances sont favorables, à la famille de fonctions `str` normale, aux fonctions MBCS ou aux fonctions Unicode, comme décrit dans « Portabilité MBCS/Unicode ».  
  
 Portabilité MBCS/Unicode  
 Avec le fichier d'en-tête Tchar.h, vous pouvez créer des applications codées sur un octet, MBCS et Unicode à partir des mêmes sources. Tchar.h définit des macros préfixées avec *_tcs* , qui est mappé à `str`, `_mbs`, ou *wcs* fonctions, comme il convient. Pour générer du MBCS, définissez le symbole **_MBCS**. Pour générer du Unicode, définissez le symbole **_UNICODE**. Par défaut, **_MBCS** est défini pour les applications MFC. Pour plus d’informations, consultez [des mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
> [!NOTE]
>  Comportement n’est pas défini si vous définissez à la fois **_UNICODE** et **_MBCS**.  
  
 Les fichiers d'en-tête Mbctype.h et Mbstring.h définissent les fonctions et macros propres à MBCS, dont vous pouvez avoir besoin dans certains cas. Par exemple, `_ismbblead` vous indique si un octet spécifique dans une chaîne est un octet de tête.  
  
 Pour une portabilité internationale, codez votre programme avec [Unicode](../text/support-for-unicode.md) ou jeux de caractères multioctets (MBCS).  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Activer MBCS dans mon programme](../text/international-enabling.md)  
  
-   [Activer Unicode et MBCS dans mon programme](../text/internationalization-strategies.md)  
  
-   [Utiliser MBCS pour créer un programme internationalisé](../text/mbcs-programming-tips.md)  
  
-   [Afficher un résumé de la programmation MBCS](../text/mbcs-programming-tips.md)  
  
-   [En savoir plus sur les mappages de texte générique pour la portabilité de la largeur en octets](../text/generic-text-mappings-in-tchar-h.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)   
 [Prise en charge MBCS dans Visual C++](../text/mbcs-support-in-visual-cpp.md)