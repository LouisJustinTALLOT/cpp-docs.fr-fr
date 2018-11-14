---
title: Configuration d’un lien statique vers le Code d’inscription (C++ uniquement)
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: 11600b47abbbd247d099d871fce5e9d5d17d3cf4
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327887"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configuration d’un lien statique vers le Code d’inscription (C++ uniquement)

Les clients C++ peuvent créer un lien statique vers le code de Registrar. Liaison statique de l’Analyseur de Registrar ajoute environ 5 Ko à une version Release.

La méthode la plus simple pour définir une liaison statique suppose que vous avez spécifié [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) dans la déclaration de votre objet. (Il s’agit de la spécification par défaut utilisée par ATL.)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Pour créer un lien statique à l’aide de DECLARE_REGISTRY_RESOURCEID

1. Spécifiez [/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_statique\_Registre** au lieu de **/D \_ATL\_DLL**.

1. Recompilez.

## <a name="see-also"></a>Voir aussi

[Composant de Registre (inscription)](../atl/atl-registry-component-registrar.md)
