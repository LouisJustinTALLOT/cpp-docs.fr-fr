---
description: 'En savoir plus sur : attributs (C++/CX)'
title: Attributs (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 82299db6b5c11521584b8dd400b401ec0df78c72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302775"
---
# <a name="attributes-ccx"></a>Attributs (C++/CX)

Un attribut est un type spécial de classe ref qui peut être ajouté entre crochets aux types Windows Runtime et aux méthodes pour spécifier certains comportements lors de la création de métadonnées. Plusieurs attributs prédéfinis, par exemple  [Windows :: Foundation :: Metadata :: WebHostHidden](/uwp/api/windows.foundation.metadata.webhosthiddenattribute), sont couramment utilisés dans le code C++/CX. Cet exemple montre comment l'attribut est appliqué à une classe :

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Attributs personnalisés

Vous pouvez également définir des attributs personnalisés. Les attributs personnalisés doivent se conformer aux règles de Windows Runtime suivantes :

- Les attributs personnalisés ne peuvent contenir que des champs publics.

- Les champs d'attributs personnalisés peuvent être initialisés lorsque l'attribut est appliqué à une classe.

- Un champ peut être l'un de ces types :

  - int32 (entier)

  - uint32 (entier non signé)

  - bool

  - Platform::String^

  - Windows::Foundation::HResult

  - Platform::Type^

  - classe Enum publique (inclut des énumérations définies par l'utilisateur)

L'exemple suivant indique comment définir un attribut personnalisé et l'initialiser pour l'utiliser.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Voir aussi

[Système de type (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)
