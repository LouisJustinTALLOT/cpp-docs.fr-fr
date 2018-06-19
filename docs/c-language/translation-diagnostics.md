---
title: 'Translation : Diagnostics | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c6a59abc48e5a6bc2aa727508b61abe120c8425
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385151"
---
# <a name="translation-diagnostics"></a>Translation : Diagnostics
**ANSI 2.1.1.3** Comment un diagnostic est identifié  
  
 Microsoft C génère des messages d'erreur au format suivant :  
  
```  
  
filename( line-number ) : diagnostic Cnumbermessage  
```  
  
 où *filename* est le nom du fichier source dans lequel l'erreur est survenue. *line-number* correspond au numéro de ligne auquel le compilateur a détecté l'erreur. `diagnostic` est une erreur ou un avertissement. `number` est un seul nombre à quatre chiffres (précédé d'un **C**, comme indiqué dans la syntaxe) qui identifie l'erreur ou l'avertissement. `message` est un message explicatif.  
  
## <a name="see-also"></a>Voir aussi  
 [Comportement défini par l’implémentation](../c-language/implementation-defined-behavior.md)