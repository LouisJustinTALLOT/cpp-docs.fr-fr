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
ms.openlocfilehash: ea84b46e31d57ec05bf9641674d045f531b04722
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593750"
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
 [Contextes d’attribut](../windows/attribute-contexts.md)  
 [Attributs par groupe](../windows/attributes-by-group.md)