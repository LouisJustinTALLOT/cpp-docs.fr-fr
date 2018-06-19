---
title: . DOSSEG | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3817cfe98758faf86ea87d74e02657598c3e806b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054882"
---
# <a name="dosseg"></a>.DOSSEG
Trie les segments en fonction de la convention de segment MS-DOS : CODE en premier lieu, puis les segments n’est pas dans DGROUP et puis segments dans DGROUP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.DOSSEG  
  
```  
  
## <a name="remarks"></a>Notes  
 Les segments dans DGROUP suivent cet ordre : segments pas BSS ou de la pile, les segments BSS et segments de pile. Principalement utilisé pour assurer la prise en charge de CodeView dans les programmes autonomes MASM. Identique à [DOSSEG](../../assembler/masm/dosseg.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)