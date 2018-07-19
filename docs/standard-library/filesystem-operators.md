---
title: '&lt;filesystem&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e93cbd4298a0f2094c2c5950220610a17642512
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965576"
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

## <a name="see-also"></a>Voir aussi

[Path, classe (bibliothèque C++ Standard)](../standard-library/path-class.md)<br/>
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
