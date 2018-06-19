---
title: Contextes d’attribut | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], contexts
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e220eb0e7eb80d01d70aed82e773c46fe6704c7d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860331"
---
# <a name="attribute-contexts"></a>Contextes d'attribut
Attributs C++ peuvent être décrite à l’aide de quatre champs de base : la cible peuvent être appliquées aux (**s’applique à**), si elles sont renouvelables ou non (**Repeatable**), le requis la présence d’autres attributs ( **Attributs obligatoires**) et les incompatibilités avec les autres attributs (**attributs non valides**). Ces champs sont répertoriés dans une table qui l’accompagne dans la rubrique de référence de chaque attribut. Chacun de ces champs est décrit ci-dessous.  
  
## <a name="applies-to"></a>S'applique à  
 Ce champ décrit les différents éléments de langage C++ juridique cibles pour l’attribut spécifié. Par exemple, si un attribut spécifie « classe » dans le **s’applique à** champ, cela indique que l’attribut peut uniquement être appliqué à une classe C++ conforme. Si l’attribut est appliqué à une fonction membre d’une classe, une erreur de syntaxe entraînera.  
  
 Pour plus d’informations, consultez [attributs par utilisation](../windows/attributes-by-usage.md).  
  
## <a name="repeatable"></a>Renouvelable  
 Ce champ indique si l’attribut peut être appliqué à plusieurs reprises sur la même cible. La plupart des attributs ne peuvent pas être répétés.  
  
## <a name="required-attributes"></a>Attributs requis  
 Ce champ répertorie les autres attributs qui doivent être présents (c'est-à-dire, appliquée à la même cible) pour l’attribut spécifié fonctionner correctement. Il est rare qu’un attribut pour que toutes les entrées de ce champ.  
  
## <a name="invalid-attributes"></a>Attributs non valides  
 Ce champ répertorie les autres attributs qui ne sont pas compatibles avec l’attribut spécifié. Il est rare qu’un attribut pour que toutes les entrées de ce champ.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des attributs C++](../windows/cpp-attributes-reference.md)