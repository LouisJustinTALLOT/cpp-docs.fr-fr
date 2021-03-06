---
description: 'En savoir plus sur : les &lt; typedefs d’exception &gt;'
title: '&lt;exception&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: 5df3f49a66cced171d96c2dedad7b239535519a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324527"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt;, typedefs

## <a name="exception_ptr"></a><a name="exception_ptr"></a> exception_ptr

Type qui décrit un pointeur vers une exception.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Notes

Une classe interne non spécifiée utilisée pour implémenter le type `exception_ptr`.

Utilisez un objet `exception_ptr` pour référencer l'exception actuelle ou une instance d'une exception spécifiée par l'utilisateur. Dans l’implémentation Microsoft, une exception est représentée par une structure [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record). Chaque objet `exception_ptr` inclut un champ de référence d'exception qui pointe vers une copie de la structure `EXCEPTION_RECORD` qui représente l'exception.

Lorsque vous déclarez une variable `exception_ptr`, la variable n'est associée à aucune exception. Autrement dit, son champ de référence d'exception est NULL. Ce type d’objet `exception_ptr` est appelé *exception_ptr null*.

Utilisez la fonction `current_exception` ou `make_exception_ptr` pour assigner une exception à un objet `exception_ptr`. Lorsque vous assignez une exception à une variable `exception_ptr`, le champ de référence de l'exception de la variable pointe vers une copie de l'exception. Si la mémoire est insuffisante pour copier l’exception, le champ de référence d’exception pointe vers une copie d’une exception [std::bad_alloc](../standard-library/bad-alloc-class.md). Si la `current_exception` `make_exception_ptr` fonction ou ne peut pas copier l’exception pour une autre raison, la fonction appelle la `terminate` fonction CRT pour quitter le processus en cours.

En dépit de son nom, un objet `exception_ptr` n'est pas lui-même un pointeur. Il ne respecte pas la sémantique des pointeurs et ne peut pas être utilisé avec les accès des membres pointeurs (`->`) ou des opérateurs d’indirection (*). L'objet `exception_ptr` n'a aucune donnée membre ou fonction membre publique.

**Comparaisons**

Vous pouvez utiliser les opérateurs Égal à (`==`) et Non égal à (`!=`) pour comparer deux objets `exception_ptr`. Les opérateurs ne comparent pas la valeur binaire (modèle binaire) des structures `EXCEPTION_RECORD` qui représentent les exceptions. À la place, les opérateurs comparent les adresses dans le domaine de référence d'exception des objets `exception_ptr`. Par conséquent, une exception `exception_ptr` null et la valeur NULL sont considérées comme égales.

## <a name="terminate_handler"></a><a name="terminate_handler"></a> terminate_handler

Type qui décrit un pointeur vers une fonction appropriée pour une utilisation en tant que `terminate_handler`.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Notes

Le type décrit un pointeur vers une fonction appropriée devant être utilisée en tant que gestionnaire d'arrêt.

### <a name="example"></a>Exemple

Consultez [set_terminate](../standard-library/exception-functions.md#set_terminate) pour obtenir un exemple d’utilisation de `terminate_handler`.

## <a name="unexpected_handler"></a><a name="unexpected_handler"></a> unexpected_handler

Le type décrit un pointeur vers une fonction pouvant être utilisée comme `unexpected_handler`.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Exemple

Consultez [set_unexpected](../standard-library/exception-functions.md#set_unexpected) pour obtenir un exemple d’utilisation de `unexpected_handler`.
