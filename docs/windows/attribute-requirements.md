---
title: Configuration requise d’attribut | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: e42ca06f-5f3c-40b5-972a-39ecf522d227
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0aa52f77403602d7f63f39b19e05186a9cea7c9d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424666"
---
# <a name="attribute-requirements"></a>Exigences des attributs

La configuration requise pour les attributs C++ décrire les types de projets, de paramètres de compilateur et d’autres informations nécessaires pour un attribut fonctionne. Les catégories d’informations sont décrits ci-dessous.
  
> [!NOTE]
> À l’aide des attributs sur une classe qui dérive d’une classe qui utilise également des attributs n’est pas pris en charge.
  
## <a name="header"></a>Header

Ce champ répertorie les fichiers d’en-tête qui doivent être inclus avant un attribut peut être utilisé.
  
## <a name="project"></a>Projet

Ce champ décrit les types de projets dans lesquels un attribut peut être utilisé.
  
## <a name="compiler"></a>Compilateur

Ce champ fournit les options du compilateur qui doivent être présentes pour cet attribut à utiliser.
  
## <a name="see-also"></a>Voir aussi

[Contextes d’attribut](../windows/attribute-contexts.md)<br/>
[Attributs par groupe](../windows/attributes-by-group.md)