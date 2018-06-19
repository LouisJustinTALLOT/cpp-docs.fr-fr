---
title: Opérateurs de préprocesseur | Documents Microsoft
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
ms.openlocfilehash: da6ff2a87007892cb5a76e7fc003e1d172056fb0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839336"
---
# <a name="preprocessor-operators"></a>Opérateurs de préprocesseur
Quatre opérateurs propres au préprocesseur sont utilisées dans le contexte de la `#define` directive (voir la liste suivante pour obtenir un récapitulatif de chaque). Les opérateurs d’enchaînement charizing et collage de jeton sont décrites dans les trois sections suivantes. Pour plus d’informations sur la **défini** (opérateur), consultez [le #if, #elif, #else et #endif Directives](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
|Opérateur|Action|  
|--------------|------------|  
|[Opérateur d’enchaînement (#)](../preprocessor/stringizing-operator-hash.md)|Provoque l’argument réel correspondant à être placés entre guillemets doubles|  
|[Opérateur charizing (#@)](../preprocessor/charizing-operator-hash-at.md)|Provoque l’argument correspondant à être placés entre guillemets simples et est traitée comme un caractère (Specific Microsoft)|  
|[Opérateur de collage de jeton (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Autorise les jetons sont utilisés en tant qu’arguments réels pour être concaténées pour former d’autres jetons|  
|[Defined (opérateur)](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifie l’écriture des expressions composées dans certaines directives de macro|  
  
## <a name="see-also"></a>Voir aussi  
 [Directives de préprocesseur](../preprocessor/preprocessor-directives.md)   
 [Macros prédéfinies](../preprocessor/predefined-macros.md)   
 [Informations de référence sur le préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)