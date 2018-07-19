---
title: enable_if, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::enable_if
dev_langs:
- C++
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2192ea954df1e7a63157d6deb04c7d34cd42337c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966483"
---
# <a name="enableif-class"></a>enable_if, classe

Crée une instance d’un type pour une résolution de surcharge SFINAE sous certaines conditions. Le typedef imbriqué `enable_if<Condition,Type>::type` existe, et est un synonyme de `Type`— si et seulement si `Condition` est **true**.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Paramètres

*B* la valeur qui détermine l’existence du type résultant.

*T* type à instancier si *B* a la valeur true.

## <a name="remarks"></a>Notes

Si *B* a la valeur true, `enable_if<B, T>` possède un typedef imbriqué nommé « type » qui est un synonyme de *T*.

Si *B* a la valeur false, `enable_if<B, T>` n’a pas un typedef imbriqué nommé « type ».

Le modèle d'alias suivant est fourni :

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

En C++, l’échec du remplacement des paramètres de modèle n’est pas une erreur en soi : il est désigné sous le nom de *SFINAE* (Substitution Failure Is Not An Error). En règle générale, `enable_if` permet de supprimer des candidats de la résolution de surcharge (autrement dit, elle trie l'ensemble des surcharges) pour qu'une définition puisse être rejetée en faveur d'une autre. Cette opération est conforme au comportement SFINAE. Pour plus d’informations sur SFINAE, consultez [Substitution failure is not an error](http://go.microsoft.com/fwlink/p/?linkid=394798) (l’échec du remplacement n’est pas une erreur) sur Wikipedia.

Voici quatre exemples de scénarios :

- Scénario 1 : Encapsulation du type de retour d'une fonction :

```cpp
    template <your_stuff>
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
 }
// The alias template makes it more concise:
    template <your_stuff>
enable_if_t<your_condition, your_return_type>
yourfunction(args) {// ...
 }
```

- Scénario 2 : Ajout d'un paramètre de fonction qui a un argument par défaut :

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
 }
```

- Scénario 3 : Ajout d'un paramètre de modèle qui a un argument par défaut :

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Scénario 4 : Si votre fonction a un argument non basé sur un modèle, vous pouvez encapsuler son type :

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
 }
```

Le scénario 1 ne fonctionne pas avec des constructeurs ni des opérateurs de conversion, car ils n'ont pas de types de retour.

Le scénario 2 laisse le paramètre sans nom. Vous pouvez dire `::type Dummy = BAR`, mais le nom `Dummy` n'est pas pertinent et l'affectation d'un nom risque de déclencher un avertissement de type « paramètre non référencé ». Vous devez choisir un type de paramètre de fonction `FOO` et un argument par défaut `BAR`.  Vous pouvez dire **int** et `0`, mais ensuite les utilisateurs de votre code peuvent par inadvertance passer à la fonction un entier supplémentaire qui serait ignoré. Au lieu de cela, nous vous recommandons d’utiliser `void **` et `0` ou **nullptr** , car presque rien n’est pas convertible en `void **`:

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

Le scénario 2 fonctionne également pour les constructeurs ordinaires.  Toutefois, il ne fonctionne pas pour les opérateurs de conversion, car ils ne peuvent pas accepter de paramètres supplémentaires.  Il ne fonctionne pas non plus pour les constructeurs [variadic](../cpp/ellipses-and-variadic-templates.md), car l’ajout de paramètres supplémentaires transforme le package de paramètres de fonction en contexte non déduit et va ainsi à l’encontre de l’objectif de `enable_if`.

Le scénario 3 utilise le nom `Dummy`, mais il est facultatif. « `typename = typename` » seul fonctionne, mais si cela vous semble bizarre, vous pouvez utiliser un nom « factice » : simplement, n’utilisez pas de nom qui pourrait aussi être utilisé dans la définition de fonction. Si vous n'affectez pas de type à `enable_if`, la valeur par défaut est void et cela est parfaitement judicieux car vous ne vous souciez pas de `Dummy`. Cela fonctionne pour tout, y compris les opérateurs de conversion et les constructeurs [variadic](../cpp/ellipses-and-variadic-templates.md).

Le scénario 4 fonctionne dans les constructeurs sans type de retour et résout ainsi la limite d’encapsulation du scénario 1.  Toutefois, le scénario 4 est limité à des arguments de fonction non basés sur un modèle, qui ne sont pas toujours disponibles.  (L'utilisation du scénario 4 sur un argument de fonction basé sur un modèle empêche le fonctionnement de la déduction de l'argument de modèle.)

`enable_if` est puissante, mais aussi dangereuse en cas d'utilisation inappropriée.  Comme son objectif est de faire disparaître les candidats avant la résolution de surcharge, ses effets peuvent être très déroutants si elle est mal utilisée.  Voici quelques recommandations :

- N'utilisez pas `enable_if` pour choisir entre les implémentations au moment de la compilation. N'écrivez jamais une classe `enable_if` pour `CONDITION` et une autre pour `!CONDITION`.  Utilisez plutôt un modèle de *répartition d’étiquette*, par exemple, un algorithme qui sélectionne des implémentations en fonction des points forts des itérateurs donnés.

- N'utilisez pas `enable_if` pour appliquer une configuration requise.  Si vous voulez valider les paramètres de modèle et que la validation échoue, causant une erreur au lieu de donner la possibilité de sélectionner une autre implémentation, utilisez [static_assert](../cpp/static-assert.md).

- Utilisez `enable_if` quand un ensemble de surcharges rend ambigu un code par ailleurs pertinent.  Cela se produit le plus souvent dans des constructeurs de conversion implicite.

## <a name="example"></a>Exemple

Cet exemple explique comment la fonction de modèle de bibliothèque C++ Standard [std::make_pair()](../standard-library/utility-functions.md#make_pair) tire parti de `enable_if`.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

Dans cet exemple, `make_pair("foo", "bar")` retourne `pair<const char *, const char *>`. La résolution de surcharge doit déterminer l'élément `func()` voulu. `pair<A, B>` a un constructeur de conversion implicite de `pair<X, Y>`.  Cela n'est pas nouveau et figurait déjà dans C++98. Toutefois, dans C++98/03, la signature du constructeur de conversion implicite existe toujours, même s'il s'agit de `pair<int, int>(const pair<const char *, const char *>&)`.  Résolution de surcharge ne se soucie pas qu’une tentative d’instanciation de ce constructeur éclate anticiper car `const char *` n’est pas implicitement convertible en **int**; elle examine uniquement les signatures, avant la fonction sont des définitions instancié.  Ainsi, l'exemple de code est ambigu, car des signatures existent pour convertir `pair<const char *, const char *>` à la fois en `pair<int, int>` et `pair<string, string>`.

C++11 a résolu cette ambiguïté en utilisant `enable_if` pour garantir que `pair<A, B>(const pair<X, Y>&)` existe **uniquement** quand `const X&` est implicitement convertible en `A` et que `const Y&` est implicitement convertible en `B`.  Cela permet à la résolution de surcharge de déterminer que `pair<const char *, const char *>` n'est pas convertible en `pair<int, int>` et que la surcharge qui accepte `pair<string, string>` est valide.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
