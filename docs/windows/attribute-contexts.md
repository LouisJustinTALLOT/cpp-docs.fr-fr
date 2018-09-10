---
title: Contextes d’attribut | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e3935b168220b528afaecd2e1438cfe49496b1b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313661"
---
# <a name="attribute-contexts"></a>Contextes d'attribut
Attributs C++ peuvent être décrits à l’aide de quatre champs de base : la cible, elles peuvent être appliquées à (**s’applique à**), si elles sont renouvelables ou non (**Repeatable**), le requis la présence d’autres attributs ( **Attributs requis**) et les incompatibilités avec d’autres attributs (**attributs non valides**). Ces champs sont répertoriés dans une table qui accompagne cet article dans la rubrique de référence de chaque attribut. Chacun de ces champs est décrite ci-dessous.
  
## <a name="applies-to"></a>S'applique à
 Ce champ décrit les éléments de langage C++ différents qui sont des cibles juridiques pour l’attribut spécifié. Par exemple, si un attribut spécifie « classe » dans le **s’applique à** champ, cela indique que l’attribut peut uniquement être appliqué à une classe C++ juridique. Si l’attribut est appliqué à une fonction membre d’une classe, une erreur de syntaxe est générée.
  
 Pour plus d’informations, consultez [attributs par utilisation](../windows/attributes-by-usage.md).
  
## <a name="repeatable"></a>Renouvelable
 Ce champ indique si l’attribut peut être appliqué à plusieurs reprises sur la même cible. La majorité des attributs ne sont pas reproductibles.
  
## <a name="required-attributes"></a>Attributs requis
 Ce champ répertorie les autres attributs qui doivent être présents (est, appliqué à la même cible) pour l’attribut spécifié fonctionner correctement. Il est rare qu’un attribut d’avoir toutes les entrées pour ce champ.
  
## <a name="invalid-attributes"></a>Attributs non valides
 Ce champ répertorie les autres attributs qui ne sont pas compatibles avec l’attribut spécifié. Il est rare qu’un attribut d’avoir toutes les entrées pour ce champ.
  
## <a name="see-also"></a>Voir aussi
 [Référence des attributs C++](../windows/cpp-attributes-reference.md)