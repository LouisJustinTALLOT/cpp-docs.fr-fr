---
title: TypeName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77e3cc6f9691cf071a420ee2659c713f9e28036f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061589"
---
# <a name="typename"></a>typename

Dans les définitions de modèle, indique au compilateur qu’un identificateur inconnu est un type. Dans les listes de paramètres de modèle, permet de spécifier un paramètre de type.

## <a name="syntax"></a>Syntaxe

```
typename identifier;
```

## <a name="remarks"></a>Notes

Ce mot clé doit être utilisé si un nom dans une définition de modèle est un nom qualifié qui dépend d’un argument de modèle ; Il est facultatif si le nom qualifié n’est pas dépendant. Pour plus d’informations, consultez [modèles et résolution de noms](../cpp/templates-and-name-resolution.md).

**TypeName** peut être utilisée par n’importe quel type de n’importe où dans une définition ou déclaration de modèle. Il n’est pas autorisé dans la liste des classes de base sauf sous forme d’argument template pour une classe de base de modèle.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

Le **typename** mot clé peut également être utilisé à la place de **classe** dans le paramètre de modèle des listes. Par exemple, les instructions suivantes sont sémantiquement équivalentes :

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