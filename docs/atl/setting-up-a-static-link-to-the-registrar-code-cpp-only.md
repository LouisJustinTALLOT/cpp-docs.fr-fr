---
title: Configuration d’un lien statique vers le Code d’inscription (C++ uniquement) | Microsoft Docs
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
ms.openlocfilehash: 7a66ca33aa95ea6ffd59860cf0a55e51266ef5cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757696"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configuration d’un lien statique vers le Code d’inscription (C++ uniquement)

Les clients C++ peuvent créer un lien statique vers le code de Registrar. Liaison statique de l’Analyseur de Registrar ajoute environ 5 Ko à une version Release.

La méthode la plus simple pour définir une liaison statique suppose que vous avez spécifié [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) dans la déclaration de votre objet. (Il s’agit de la spécification par défaut utilisée par ATL.)

### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Pour créer un lien statique à l’aide de DECLARE_REGISTRY_RESOURCEID

1. Spécifiez [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` au lieu de /D **_ATL_DLL**.

2. Recompilez.

## <a name="see-also"></a>Voir aussi

[Composant de Registre (inscription)](../atl/atl-registry-component-registrar.md)

