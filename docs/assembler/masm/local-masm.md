---
title: LOCAL (MASM) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed9926d23f2e1e8636f31a6f586609ae22d38acd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053569"
---
# <a name="local-masm"></a>LOCAL (MASM)
Dans la première directive, au sein d’une macro, **LOCAL** définit les étiquettes qui sont uniques à chaque instance de la macro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>Notes  
 Dans la deuxième directive, au sein d’une définition de procédure (**PROC**), **LOCAL** crée des variables de pile qui existent pour la durée de la procédure. Le *étiquette* peut être une simple variable ou un tableau contenant *nombre* éléments.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)