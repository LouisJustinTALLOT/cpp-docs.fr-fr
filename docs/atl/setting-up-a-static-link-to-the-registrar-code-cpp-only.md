---
title: Configuration d’un lien statique vers le Code d’inscription (C++ uniquement)
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: e5f09ce4626e030c43ecc30ca44d1ac738341c6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557407"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configuration d’un lien statique vers le Code d’inscription (C++ uniquement)

Les clients C++ peuvent créer un lien statique vers le code de Registrar. Liaison statique de l’Analyseur de Registrar ajoute environ 5 Ko à une version Release.

La méthode la plus simple pour définir une liaison statique suppose que vous avez spécifié [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) dans la déclaration de votre objet. (Il s’agit de la spécification par défaut utilisée par ATL.)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Pour créer un lien statique à l’aide de DECLARE_REGISTRY_RESOURCEID

1. Spécifiez [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` au lieu de /D **_ATL_DLL**.

1. Recompilez.

## <a name="see-also"></a>Voir aussi

[Composant de Registre (inscription)](../atl/atl-registry-component-registrar.md)
