---
title: '&lt;filesystem&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
ms.openlocfilehash: 819c91e707e50a190aa58eda62f8e07f3451b033
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240729"
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt;, opérateurs

Les opérateurs exécutent une comparaison lexicale de deux chemins d'accès sous forme de chaînes. Utilisez le `equivalent` fonction permettant de déterminer si deux chemins d’accès (par exemple, un chemin d’accès relatif et un chemin d’accès absolu) font référence au même fichier ou répertoire sur le disque.

Pour plus d’informations, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

La fonction retourne left.native() == right.native().

## <a name="operator"></a>!=, opérateur

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

La fonction retourne !(left == right).

## <a name="operator"></a>< (opérateur)

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

La fonction retourne left.native() < right.native().

## <a name="operator"></a><= (opérateur)

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

La fonction retourne !(right \< left).

## <a name="operator"></a>> (opérateur)

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

La fonction retourne right \< left.

## <a name="operator"></a>>= (opérateur)

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

La fonction retourne !(left < right).

## <a name="operator"></a>operator/

```cpp
path operator/(const path& left, const path& right);
```

La fonction exécute :

```cpp
basic_string<Elem, Traits> str;
path ans = left;
return (ans /= right);
```

## <a name="operator"></a><<, opérateur

```cpp
template <class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```

La fonction retourne os << pval.string\<Elem, Traits>().

## <a name="operator"></a>>>, opérateur

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

La fonction exécute :

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```
