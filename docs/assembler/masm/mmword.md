---
title: MMWORD | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e97b1e58116d633519b1a780928e05862ac1771d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054778"
---
# <a name="mmword"></a>MMWORD
Utilisé pour les opérandes de multimédias 64 bits avec des instructions MMX et SSE (XMM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>Notes  
 `MMWORD` est un type.  Avant de MMWORD ajouté à MASM, une fonctionnalité équivalente pourrait avoir été obtenue avec :  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Alors que les deux instructions fonctionnent sur les opérandes de 64 bits, `QWORD` est de type pour les entiers non signés 64 bits et `MMWORD` est le type de valeur multimédia 64 bits.  
  
 `MMWORD` est destiné à représenter le même type que [__m64](../../cpp/m64.md).  
  
## <a name="example"></a>Exemple  
  
```  
movq     mm0, mmword ptr [ebx]  
```