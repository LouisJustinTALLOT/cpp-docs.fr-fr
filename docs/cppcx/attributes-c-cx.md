---
title: Attributs (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 437432ce32497311a9a91237118d6088881662a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371882"
---
# <a name="attributes-ccx"></a>Attributs (C++/CX)

Un attribut est un type spécial de classe ref qui peut être prépended dans les parenthèses carrées aux types et méthodes De Windows Runtime pour spécifier certains comportements dans la création de métadonnées. Plusieurs attributs prédéfinis, par [exemple, Windows::Foundation::Metadata::WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)- sont couramment utilisés dans le code C/CX. Cet exemple montre comment l'attribut est appliqué à une classe :

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Attributs personnalisés

Vous pouvez également définir des attributs personnalisés. Les attributs personnalisés doivent être conformes à ces règles Windows Runtime :

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
[Référence linguistique CMD/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence aux espaces de noms](../cppcx/namespaces-reference-c-cx.md)
