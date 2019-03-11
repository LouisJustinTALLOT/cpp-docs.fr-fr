---
title: Déconseiller des types et des membres (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 7f488dfa522c0b48c75150d40584b0946baae806
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748448"
---
# <a name="deprecating-types-and-members-ccx"></a>Déconseiller des types et des membres (C++/CX)

En C / c++ / CX, le fait de déconseiller des types Windows Runtime et des membres pour les producteurs et consommateurs à l’aide de la [déconseillées](/uwp/api/windows.foundation.metadata.deprecatedattribute) attribut est pris en charge. Si vous consommez une API à laquelle cet attribut a été appliqué, vous recevez un message d'avertissement au moment de la compilation qui indique que l'API est déconseillée et recommande l'utilisation d'une autre API. Dans vos propres types et méthodes publics, vous pouvez appliquer cet attribut et fournir votre message personnalisé.

> [!CAUTION]
> Le [déconseillées](/uwp/api/windows.foundation.metadata.deprecatedattribute) attribut doit être utilisé uniquement avec les types Windows Runtime. Pour les classes et les membres C++ standard, utilisez [__declspec(deprecated)](../cpp/deprecated-cpp.md).

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

| |
|-|
|Contrôle XAML|
|délégué|
|événement|
|champ enum|
|enum|
|struct|
|méthode|
|class|
|interface|
|propriété|
|champ struct|
|constructeur paramétrable|

## <a name="see-also"></a>Voir aussi

[Système de type](../cppcx/type-system-c-cx.md)<br/>
[Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)
