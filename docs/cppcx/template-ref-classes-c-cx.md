---
title: "Classes ref de modèle (C + c++ / CX) | Documents Microsoft"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f135907a4aba473db62734f9370ee82b7113c66d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="template-ref-classes-ccx"></a>Classes ref de modèle (C++/CX)
Les modèles C++ ne sont pas publiés aux métadonnées et ne peuvent donc pas avoir une accessibilité publique ou protégée dans votre programme. Vous pouvez, bien sûr, utiliser les modèles C++ standard en interne dans votre programme. En outre, vous pouvez définir une classe ref privée comme un modèle et vous pouvez déclarer une classe ref de modèle explicitement spécialisé comme membre privé dans une classe ref publique.  
  
## <a name="authoring-ref-class-templates"></a>Création de modèles de classe ref  
 L'exemple suivant indique comment déclarer une classe ref privée comme modèle, et également comment déclarer un modèle C++ standard et comment déclarer les deux en tant que membres d'une classe ref publique. Notez que le modèle C++ standard peut être spécialisé par un type Windows Runtime, dans ce cas, un type Platform::String ^.  
  
 [!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]  
  
## <a name="see-also"></a>Voir aussi  
 [Système de type (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)