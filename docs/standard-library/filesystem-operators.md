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
ms.openlocfilehash: 546e601afeb05e0347dba8bf792611f20068c69b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt;, opérateurs

Les opérateurs exécutent une comparaison lexicale de deux chemins d'accès sous forme de chaînes. Utilisez la fonction **equivalent** pour déterminer si deux chemins d'accès (par exemple, un chemin d'accès relatif et un chemin d'accès absolu) font référence au même fichier ou répertoire sur le disque.

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

[Path, classe (bibliothèque Standard C++)](../standard-library/path-class.md)<br/>
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
