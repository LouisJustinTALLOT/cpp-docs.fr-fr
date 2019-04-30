---
title: Chaînes (C++/CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: 8f7cbdd02cb1d38231c476ba939009a95533a046
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403241"
---
# <a name="strings-ccx"></a>Chaînes (C++/CX)

Texte dans le Windows Runtime est représenté en C / c++ / CX par le [classe Platform::String](../cppcx/platform-string-class.md). Utilisez le `Platform::String Class` lorsque vous passez des chaînes dans les deux sens aux méthodes dans des classes Windows Runtime, ou lorsque vous interagissez avec d’autres composants Windows Runtime dans la limite (ABI) de l’interface binaire d’application. La `Platform::String Class` fournit des méthodes pour plusieurs opérations de chaînes courantes mais elle n'est pas conçue pour être une classe de chaîne complète. Dans votre module C++, utilisez les types de chaînes C++ standard tels que [wstring](../standard-library/basic-string-class.md) pour tout traitement de texte significatif, puis convertissez le résultat final en [Platform::String^](../cppcx/platform-string-class.md) avant de le passer vers ou à partir d'une interface publique. Il est facile et efficace de convertir entre `wstring` ou `wchar_t*` et `Platform::String`.

**Passage rapide**

Dans certains cas, le compilateur peut vérifier qu'il peut sans risque construire une `Platform::String` ou passer une `String` à une fonction sans copier les données de chaîne sous-jacentes. Ces opérations sont appelées *passage rapide* et elles se produisent de façon transparente.

## <a name="string-construction"></a>Construction de chaînes

La valeur d'un objet `String` est une séquence (en lecture seule) immuable de caractères `char16` (Unicode 16 bits). Étant donné qu'un objet `String` est immuable, l'assignation d'un nouveau littéral de chaîne à une variable d' `String` remplace en fait l'objet d'origine `String` par un nouvel objet d' `String` . Les opérations de concaténation impliquent la destruction de l'objet `String` d'origine et la création d'un nouvel objet.

**Littéraux**

Un *caractère littéral* est un caractère placé entre guillemets simples et une *chaîne littérale* est une séquence de caractères placée entre guillemets doubles. Si vous utilisez un littéral pour initialiser une variable String^, le compilateur suppose que le littéral est constitué de caractères `char16` . Ainsi, vous ne devez pas faire précéder le littéral par le modificateur de chaîne « L » ou le placer dans une macro **_T()** ou **TEXT()** . Pour plus d'informations sur la prise en charge de C++ pour Unicode, consultez [Unicode Programming Summary](../text/unicode-programming-summary.md).

L'exemple suivant montre différentes façons de construire des objets `String` .

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>Opérations de gestion de chaînes

La classe `String` fournit des méthodes et des opérateurs pour la concaténation et comparaison de chaînes et d'autres opérations de base sur les chaînes. Pour effectuer d'autres manipulations plus étendues sur les chaînes, utilisez la fonction membre `String::Data()` pour récupérer la valeur de l'objet `String^` sous forme de `const wchar_t*`. Utilisez ensuite cette valeur pour initialiser un `std::wstring`, qui fournit des fonctions de gestion de chaînes évoluées.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>Conversions de chaînes

Une `Platform::String` ne peut contenir que des caractères `char16` ou le caractère `NULL` . Si votre application doit utiliser des caractères 8 bits, utilisez le [String::Data](../cppcx/platform-string-class.md#data) pour extraire le texte comme un `const wchar_t*`. Vous pouvez ensuite utiliser les fonctions Windows appropriées ou les fonctions de bibliothèque standard pour traiter les données et les reconvertir en un `wchar_t*` ou [wstring](../standard-library/basic-string-class.md), que vous pouvez utiliser pour construire une nouvelle `Platform::String`.

Le fragment de code suivant montre comment convertir une variable `String^` vers et à partir d'une variable `wstring` . Pour plus d'informations sur la manipulation de chaînes utilisée dans cet exemple, consultez [basic_string::replace](../standard-library/basic-string-class.md#replace).

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>Longueur de chaîne et valeurs NULL incorporées

Le [String::Length](../cppcx/platform-string-class.md#length) retourne le nombre de caractères dans la chaîne, pas le nombre d’octets. Le caractère NULL de fin n'est pas compté, sauf si vous le spécifiez explicitement lorsque vous utilisez la sémantique de pile pour construire une chaîne.

Une `Platform::String` peut contenir des valeurs NULL incorporées, mais uniquement lorsque NULL est le résultat d'une opération de concaténation. Les valeurs NULL incorporées ne sont pas prises en charge dans les littéraux de chaîne. Par conséquent, vous ne pouvez pas utiliser de valeurs NULL incorporées de cette manière pour initialiser une `Platform::String`. Les valeurs NULL incorporées dans une `Platform::String` sont ignorées lorsque la chaîne est affichée, par exemple lorsqu'elle est assignée à une propriété `TextBlock::Text` . Les valeurs NULL incorporées sont supprimées quand la valeur de chaîne est retournée par la propriété `Data` .

## <a name="stringreference"></a>StringReference

Dans certains cas, votre code (a) reçoit std::wstring, ou de chaîne wchar_t ou de L » » chaîne littérale et simplement transmet à une autre méthode qui prend une chaîne ^ en tant que paramètre d’entrée. Tant que la mémoire tampon de chaîne d'origine elle-même reste valide et qu'elle ne mute pas avant le retour de la fonction, vous pouvez convertir la chaîne ou le littéral de chaîne `wchar_t*` en [Platform::StringReference](../cppcx/platform-stringreference-class.md), et le passer à la place de `Platform::String^`. Cela est autorisé, car `StringReference` dispose d'une conversion définie par l'utilisateur en `Platform::String^`. À l'aide de `StringReference` , vous pouvez éviter d'effectuer une copie supplémentaire des données de chaîne. Dans les boucles où vous passez un grand nombre de chaînes, ou lorsque vous passez des chaînes de très grande taille, vous pouvez éventuellement obtenir une amélioration significative des performances à l'aide de `StringReference`. Toutefois, dans la mesure où `StringReference` emprunte essentiellement la mémoire tampon de chaîne d'origine, vous devez faire preuve d'une grande vigilance afin d'éviter une altération de la mémoire. Ne passez pas `StringReference` à une méthode asynchrone, à moins que la chaîne d'origine ne soit dans la portée lorsque cette méthode est retournée. Un String^ initialisé à partir de StringReference force l'allocation et la copie des données de chaîne, si une seconde opération d'affectation se produit. Dans ce cas, vous perdez le gain de performances fourni par `StringReference`.

Notez que `StringReference` est un type de classe C++ standard, et non une classe ref. Vous ne pouvez pas l'utiliser dans l'interface publique des classes ref que vous définissez.

L'exemple suivant montre comment utiliser StringReference :

```
void GetDecodedStrings(std::vector<std::wstring> strings)
{
    using namespace Windows::Security::Cryptography;
    using namespace Windows::Storage::Streams;

    for (auto&& s : strings)
    {
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)
        // Call using StringReference:
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));

        //...do something with buffer
    }
}
```
