---
title: Déconseiller des types et des membres (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6d61b00690cc087c3baced6d96d0b6c8d73b5850
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040325"
---
# <a name="deprecating-types-and-members-ccx"></a>Déconseiller des types et des membres (C++/CX)

En C++/CX, la désapprobation de types et de membres de Windows Runtime pour les producteurs et les consommateurs à l’aide de l’attribut [Deprecated](/uwp/api/windows.foundation.metadata.deprecatedattribute) est prise en charge. Si vous consommez une API à laquelle cet attribut a été appliqué, vous recevez un message d'avertissement au moment de la compilation qui indique que l'API est déconseillée et recommande l'utilisation d'une autre API. Dans vos propres types et méthodes publics, vous pouvez appliquer cet attribut et fournir votre message personnalisé.

> [!CAUTION]
> L’attribut [Deprecated](/uwp/api/windows.foundation.metadata.deprecatedattribute) est destiné à être utilisé uniquement avec les types de Windows Runtime. Pour les classes et les membres C++ standard, utilisez [__declspec(deprecated)](../cpp/deprecated-cpp.md).

### <a name="example"></a>Exemple

L'exemple suivant montre comment déconseiller vos propres API publiques, par exemple dans un composant Windows Runtime. Le deuxième paramètre, de type [Windows:Foundation::Metadata::DeprecationType](/uwp/api/windows.foundation.metadata.deprecationtype) , spécifie si l'API est déconseillée ou supprimée. Actuellement, seule la valeur DeprecationType::Deprecated est prise en charge. Le troisième paramètre de l'attribut spécifie le [Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute) auquel l'attribut s'applique.

```

namespace wfm = Windows::Foundation::Metadata;

public ref class Bicycle sealed
{

public:
    property double Speed;

    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]
    double ComputeAngularVelocity();
};
```

## <a name="supported-targets"></a>Cibles prises en charge

Le tableau suivant répertorie les constructions auxquelles l'attribut Deprecated peut être appliqué :

:::row:::
   :::column span="":::
      type
      disposer
      variables
      champ enum \
      événement
      interface
   :::column-end:::
   :::column span="":::
      méthode
      constructeur paramétrable \
      property\
      modélis
      champ de struct \
      Contrôle XAML
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi

[Système de types](../cppcx/type-system-c-cx.md)<br/>
[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)
