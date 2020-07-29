---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 62e8a2026babbfea3cd1583def05a03b4bc4a229
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223510"
---
# <a name="typename"></a>typename

Dans les définitions de modèle, fournit une indication au compilateur qu’un identificateur inconnu est un type. Dans les listes de paramètres de modèle, est utilisé pour spécifier un paramètre de type.

## <a name="syntax"></a>Syntaxe

```
typename identifier;
```

## <a name="remarks"></a>Notes

Ce mot clé doit être utilisé si un nom dans une définition de modèle est un nom qualifié qui est dépendant d’un argument de modèle. elle est facultative si le nom qualifié n’est pas dépendant. Pour plus d’informations, consultez [modèles et résolution de noms](../cpp/templates-and-name-resolution.md).

**`typename`** peut être utilisé par n’importe quel type n’importe où dans une déclaration ou une définition de modèle. Il n’est pas autorisé dans la liste des classes de base sauf sous forme d’argument template pour une classe de base de modèle.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

Le **`typename`** mot clé peut également être utilisé à la place de **`class`** dans les listes de paramètres de modèle. Par exemple, les instructions suivantes sont sémantiquement équivalentes :

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>Exemple

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>Voir aussi

[Modèles](../cpp/templates-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
