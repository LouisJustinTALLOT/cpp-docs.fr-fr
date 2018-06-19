---
title: . SAFESEH | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea34448b4dae0525e7feb2fd7cca310a95a6e3c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052461"
---
# <a name="safeseh"></a>.SAFESEH
Enregistre une fonction en tant que gestionnaire d’exceptions structuré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.SAFESEH identifier  
```  
  
## <a name="remarks"></a>Notes  
 *identificateur* doit être l’ID pour un défini localement [PROC](../../assembler/masm/proc.md) ou [EXTRN](../../assembler/masm/extrn.md) PROC. A [étiquette](../../assembler/masm/label-masm.md) n’est pas autorisée. La barre d’outils. SAFESEH (directive) nécessite le [/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) l’option de ligne de commande ml.exe.  
  
 Pour plus d’informations sur les gestionnaires de la gestion structurée des exceptions, consultez [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).  
  
 Par exemple, pour inscrire un gestionnaire d’exceptions sécurisés, créez un nouveau fichier MASM (comme suit), assembler avec l’option /safeseh et l’ajouter à des objets liés.  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)