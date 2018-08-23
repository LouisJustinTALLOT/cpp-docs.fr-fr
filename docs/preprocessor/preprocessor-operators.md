---
title: Opérateurs de préprocesseur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fca1c097a01f34fb2cc708489338391dfced982f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539416"
---
# <a name="preprocessor-operators"></a>Opérateurs de préprocesseur
Quatre opérateurs propres au préprocesseur sont utilisés dans le contexte de la `#define` directive (voir la liste suivante pour obtenir un résumé de chaque). Les opérateurs de chaîne, de charizing et de collage de jeton sont traités dans les trois sections suivantes. Pour plus d’informations sur la `defined` opérateur, voir [le #if, #elif #else et #endif Directives](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
|Opérateur|Action|  
|--------------|------------|  
|[Opérateur d’enchaînement (#)](../preprocessor/stringizing-operator-hash.md)|Provoque l’argument réel correspondant être placée entre guillemets doubles|  
|[Opérateur charizing (#@)](../preprocessor/charizing-operator-hash-at.md)|Provoque l’argument correspondant pour être placée entre guillemets simples et doit être traité comme un caractère (Specific à Microsoft)|  
|[Opérateurs de collage de jeton (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Permet les jetons permettant d’être concaténées pour former d’autres jetons en tant qu’arguments réels|  
|[opérateur défini](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifie l’écriture des expressions composées dans certaines directives de macro|  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)   
[Macros prédéfinies](../preprocessor/predefined-macros.md)   
[Informations de référence sur le préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)