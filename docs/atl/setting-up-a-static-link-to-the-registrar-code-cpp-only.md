---
title: Configuration d’un lien statique avec le Code Registrar (C++ uniquement) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dca93c8f0fcae578700a9d9970977179fbd142d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360186"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configuration d’un lien statique avec le Code Registrar (C++ uniquement)
Les clients C++ peuvent créer un lien statique vers le code de Registrar. La liaison statique de l’Analyseur de Registrar ajoute les environ 5 Ko à une version Release.  
  
 La façon la plus simple pour configurer la liaison statique suppose que vous avez spécifié [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) dans la déclaration de votre objet. (Il s’agit de la spécification de la valeur par défaut utilisée par ATL.)  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Pour créer un lien statique en utilisant DECLARE_REGISTRY_RESOURCEID  
  
1.  Spécifiez [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` au lieu de /D **_ATL_DLL**.  
  
2.  Recompilez.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Registre (inscription)](../atl/atl-registry-component-registrar.md)

