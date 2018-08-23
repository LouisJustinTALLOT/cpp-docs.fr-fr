---
title: Stratégies d’internationalisation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d92b95cac23eed029a49239d791df237377d8376
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42587127"
---
# <a name="internationalization-strategies"></a>Stratégies d'internationalisation
En fonction de vos systèmes d’exploitation cible et les marchés, vous avez plusieurs stratégies d’internationalisation :  
  
-   Votre application utilise Unicode.  
  
     Vous utilisez des fonctionnalités spécifique à Unicode et tous les caractères sont de 16 bits (bien que vous pouvez utiliser des caractères ANSI dans certaines parties de votre programme à des fins spéciales). La bibliothèque Runtime C fournit des fonctions, macros et types de données pour la programmation Unicode uniquement. MFC prend entièrement en charge Unicode.  
  
-   Votre application utilise MBCS et peut être exécutée sur n’importe quelle plateforme Win32.  
  
     Vous utilisez des fonctionnalités spécifique à MBCS. Chaînes peuvent contenir des caractères codés sur un octet, les caractères codés sur deux ou les deux. La bibliothèque Runtime C fournit des fonctions, macros et types de données pour la programmation MBCS uniquement. MFC est entièrement compatible MBCS.  
  
-   Le code source pour votre application est écrit pour une portabilité totale, en recompilant avec le symbole `_UNICODE` ou le symbole `_MBCS` défini, vous pouvez produire des versions qui utilisent l’un. Pour plus d’informations, consultez [des mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Vous utilisez entièrement portables C Runtime fonctions, macros et types de données. La flexibilité MFC prend en charge ces stratégies.  
  
 Le reste de ces rubriques vous concentrer sur l’écriture de code portable que vous pouvez générer en Unicode ou en MBCS.  
  
## <a name="see-also"></a>Voir aussi  
 [Unicode et MBCS](../text/unicode-and-mbcs.md)   
 [Paramètres régionaux et pages de codes](../text/locales-and-code-pages.md)