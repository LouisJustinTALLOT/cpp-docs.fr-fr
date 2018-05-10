---
title: Paramètres régionaux et Pages de codes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1c7dd3c5356df7b80f21605e325158e87cc5a71
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="locales-and-code-pages"></a>Paramètres régionaux et pages de codes
Un ID de paramètres régionaux reflète les conventions et langue locales pour une région géographique spécifique. Une langue donnée peut être parlée dans plusieurs pays/région ; par exemple, le portugais est parlé au Brésil et Portugal. À l’inverse, un pays/région peut avoir plusieurs langues officiels. Par exemple, le Canada a deux langues : anglais et le Français. Par conséquent, le Canada a deux paramètres régionaux distincts : anglais (Canada) et en Français canadien. Certaines catégories dépendent des paramètres régionaux, notamment la mise en forme des dates et le format d'affichage des valeurs monétaires.  
  
 La langue détermine le texte et les données mises en forme de conventions, tandis que le pays/région détermine les conventions locales. Chaque langage a un mappage unique, représenté par les pages de codes, qui inclut des caractères autres que ceux de l’alphabet (telles que les signes de ponctuation et des nombres). Une page de codes est un jeu de caractères et est liée à la langue. Par conséquent, un [paramètres régionaux](../c-runtime-library/locale.md) est une combinaison unique de langue, pays/région et page de codes. Le paramètre de la page des paramètres régionaux et le code peut être modifié au moment de l’exécution en appelant le [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) (fonction).  
  
 Différentes langues peuvent utiliser différentes pages de codes. Par exemple, la page de codes ANSI 1252 est utilisée pour l’anglais et la plupart des langues européennes, et la page de codes ANSI 932 est utilisée pour le kanji (japonais). Pratiquement toutes les pages de codes partagent le caractère ASCII définie pour le plus bas de 128 caractères (0 x 00 à 0x7F).  
  
 N’importe quelle page de codes mono-octet peut être représentée dans un tableau (256) comme un mappage de valeurs d’octets en caractères (y compris des nombres et des signes de ponctuation) ou glyphes. N’importe quelle page de codes multioctets peut également être représentée comme une table très volumineuse (avec les entrées de 64 Ko) de caractères codés sur deux valeurs. Dans la pratique, cependant, il sont généralement représentées sous forme de tableau pour les 256 premiers caractères (codés) et de plages pour les valeurs de deux octets.  
  
 Pour plus d’informations sur les pages de code, consultez [Code Pages](../c-runtime-library/code-pages.md).  
  
 La bibliothèque Runtime C possède deux types de pages de codes internes : paramètres régionaux et multioctets. Vous pouvez modifier la page de codes en cours pendant l’exécution du programme (consultez la documentation relative à la [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) et [_setmbcp](../c-runtime-library/reference/setmbcp.md) fonctions). En outre, la bibliothèque Runtime peut obtenir et utiliser la valeur de la page de codes du système d’exploitation est constante pour la durée de l’exécution du programme.  
  
 Lorsque la page de codes des paramètres régionaux change, le comportement de l’ensemble de dépendant des paramètres régionaux des fonctions change en fonction de la page de codes choisie. Par défaut, toutes les fonctions dépendant des paramètres régionaux commencent l’exécution avec une page de codes des paramètres régionaux unique pour les paramètres régionaux « C ». Vous pouvez modifier la page de codes des paramètres régionaux interne (ainsi que d’autres propriétés spécifiques aux paramètres régionaux) en appelant le `setlocale` (fonction). Un appel à `setlocale`(LC_ALL, « ») définit les paramètres régionaux à celle indiquée par le système d’exploitation.  
  
 De même, lorsque la page de codes multioctets change, le comportement des fonctions multioctets change en fonction de la page de codes choisie. Par défaut, toutes les fonctions multioctets commencent l’exécution avec une page de codes multioctets correspondant à la page de codes par défaut du système d’exploitation. Vous pouvez modifier la page de codes multioctets interne en appelant le `_setmbcp` (fonction).  
  
 La fonction d’exécution C `setlocale` définit, change ou interroge tout ou partie des informations de paramètres régionaux du programme actif. Le [_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) routine est une version à caractères larges de `setlocale`; les arguments et les valeurs de retour de `_wsetlocale` sont des chaînes à caractères larges.  
  
## <a name="see-also"></a>Voir aussi  
 [Unicode et MBCS](../text/unicode-and-mbcs.md)   
 [Avantages de la portabilité d’un jeu de caractères](../text/benefits-of-character-set-portability.md)