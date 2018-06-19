---
title: Types valeur et leurs comportements (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9c05d6198b57eeee473ab7a5ec467083a5783a55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169541"
---
# <a name="value-types-and-their-behaviors-ccli"></a>Types valeur et leurs comportements (C++/CLI)
Types valeur ont été modifiés de diverses façons entre les Extensions managées pour C++ vers Visual C++. Dans cette section, nous allons le type enum du CLR et le type de classe value, ainsi que d’examiner le boxing et l’accès à l’instance boxed sur le tas CLR, ainsi que d’examiner des pointeurs intérieurs et épingles. Des modifications ont été étendues de langage dans ce domaine.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Type Enum du CLR](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 Traite des modifications dans la déclaration et le comportement des enums.  
  
 [Conversion boxing implicite de types valeur](../dotnet/implicit-boxing-of-value-types.md)  
 Explique l’objectif de conversion boxing implicite de types valeur et les suite de changements de comportement.  
  
 [Handle de suivi d’une valeur boxed](../dotnet/a-tracking-handle-to-a-boxed-value.md)  
 Décrit la conversion boxing implicite de la valeur les types se traduit par un handle de suivi à l’objet de valeur boxed.  
  
 [Sémantique de type valeur](../dotnet/value-type-semantics.md)  
 Décrit les modifications apportées à la sémantique de type valeur, y compris les méthodes virtuelles héritées, des constructeurs de classe par défaut, des pointeurs intérieurs et des pointeurs épingle.  
  
## <a name="see-also"></a>Voir aussi  
 [C + c++ / CLI Initiation à la Migration](../dotnet/cpp-cli-migration-primer.md)   
 [Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)