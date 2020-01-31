---
title: Énumérations (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: be11d8d8f38a92fbe4be00eed53dd5226bab0b59
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821751"
---
# <a name="enums-ccx"></a>Énumérations (C++/CX)

C++/CX prend en charge le mot clé `public enum class`, qui est analogue C++ à un `scoped  enum`standard. Lorsque vous utilisez un énumérateur qui est déclaré à l'aide du mot clé `public enum class` , vous devez utiliser l'identificateur d'énumération pour limiter chaque valeur de l'énumérateur.

### <a name="remarks"></a>Notes

Un `public enum class` qui n'a pas de spécificateur d'accès, tel que `public`, est traité comme un [scoped enum](../cpp/enumerations-cpp.md)C++ standard.

Une déclaration `public enum class` ou `public enum struct` peut avoir un type sous-jacent de n’importe quel type intégral bien que le Windows Runtime lui-même exige que le type soit Int32 ou UInt32 pour un enum Flags. La syntaxe suivante décrit les éléments d'un `public enum class` ou d'un `public enum struct`.

Cet exemple montre comment définir une classe d'énumération publique :

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

L'exemple suivant montre comment le consommer :

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Exemples

Les exemples suivants indiquent comment déclarer un enum,

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

L'exemple suivant indique comment effectuer un cast en équivalents numériques et effectuer des comparaisons. Notez que l'utilisation de l'énumérateur `One` est limitée par l'identificateur d'énumération `Enum1` et que l'énumérateur `First` est limité par `Enum2`.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Voir aussi

[Système de type](../cppcx/type-system-c-cx.md)<br/>
[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence aux espaces de noms](../cppcx/namespaces-reference-c-cx.md)
