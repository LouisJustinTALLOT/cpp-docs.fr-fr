---
title: Configuration d’un lien statique vers le Code d’inscription (C++ uniquement)
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: b95bd17abca3237710956f3a1bf1b1d6fa9df51e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265325"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Configuration d’un lien statique vers le Code d’inscription (C++ uniquement)

Les clients C++ peuvent créer un lien statique vers le code de Registrar. Liaison statique de l’Analyseur de Registrar ajoute environ 5 Ko à une version Release.

La méthode la plus simple pour définir une liaison statique suppose que vous avez spécifié [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) dans la déclaration de votre objet. (Il s’agit de la spécification par défaut utilisée par ATL.)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Pour créer un lien statique à l’aide de DECLARE_REGISTRY_RESOURCEID

1. Spécifiez [/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_statique\_Registre** au lieu de **/D \_ATL\_DLL**.

1. Recompilez.

## <a name="see-also"></a>Voir aussi

[Composant de Registre (inscription)](../atl/atl-registry-component-registrar.md)
