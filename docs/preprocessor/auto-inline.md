---
title: auto_inline | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc1b8a3b8539fb4871e4a28f4635c8012b9f80a2
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540803"
---
# <a name="autoinline"></a>auto_inline
Exclut toutes les fonctions définies dans la plage où **hors** est spécifié ne soit pas considérée comme des candidats pour l’expansion inline automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma auto_inline( [{on | off}] )  
```  
  
## <a name="remarks"></a>Notes  

Pour utiliser le **auto_inline** pragma, placez-le avant et immédiatement après (et non dans) une définition de fonction. Le pragma est appliqué à la première définition de fonction après détection du pragma.  
  
## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)