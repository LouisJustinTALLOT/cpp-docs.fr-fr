---
title: Établissement d’un lien statique avec le code d’inscription (C++ uniquement)
description: Comment lier de manière statique du code C++ au code d’agent de configuration ATL.
ms.date: 09/03/2020
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: f08f7d9433ae1344c7a98a5c52502d03bad21e91
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609152"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configuration d’un lien statique vers le code d’inscription (C++ uniquement)

Les clients C++ peuvent créer un lien statique vers le code du Bureau d’enregistrement. La liaison statique de l’analyseur du Bureau d’enregistrement ajoute environ 5 Ko à une version Release.

La façon la plus simple de configurer la liaison statique part du principe que vous avez spécifié [`DECLARE_REGISTRY_RESOURCEID`](reference/registry-macros.md#declare_registry_resourceid) dans la déclaration de votre objet. (Il s’agit de la spécification par défaut utilisée par la bibliothèque ATL.)

## <a name="to-create-a-static-link-using-declare_registry_resourceid"></a>Pour créer un lien statique à l’aide de `DECLARE_REGISTRY_RESOURCEID`

1. Spécifiez **`/D _ATL_STATIC_REGISTRY`** **`/D _ATL_DLL`** à la place de sur la ligne de commande cl. Pour plus d’informations, consultez [`/D`](../build/reference/d-preprocessor-definitions.md).

1. Recompiler.

## <a name="see-also"></a>Voir aussi

[Composant de Registre (registraire)](../atl/atl-registry-component-registrar.md)
