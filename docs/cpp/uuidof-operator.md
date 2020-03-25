---
title: __uuidof, opérateur
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: 09348d061fde4cb09eb6eb351f146404f355e184
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187789"
---
# <a name="__uuidof-operator"></a>__uuidof, opérateur

**Section spécifique de Microsoft**

Récupère le GUID attaché à l’expression.

## <a name="syntax"></a>Syntaxe

```
__uuidof (expression)
```

## <a name="remarks"></a>Notes

L' *expression* peut être un nom de type, un pointeur, une référence ou un tableau de ce type, un modèle spécialisé sur ces types ou une variable de ces types. L’argument est valide tant que le compilateur peut l’utiliser pour rechercher le GUID attaché.

Un cas particulier de cet intrinsèque est lorsque **0** ou null est fourni en tant qu’argument. Dans ce cas, **__uuidof** retourne un GUID composé de zéros.

Utilisez ce mot clé pour extraire le GUID attaché à :

- Objet par l’attribut étendu [UUID](../cpp/uuid-cpp.md) .

- Bloc de bibliothèque créé avec l’attribut de [module](../windows/attributes/module-cpp.md) .

> [!NOTE]
> Dans une version Debug, **__uuidof** Initialise toujours un objet de manière dynamique (au moment de l’exécution). Dans une version Release, **__uuidof** pouvez initialiser un objet de manière statique (au moment de la compilation).

Pour la compatibilité avec les versions précédentes, **_uuidof** est un synonyme de **__uuidof** sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

Le code suivant (compilé avec ole32. lib) affiche l’UUID d’un bloc de bibliothèque créé avec l’attribut de module :

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>Commentaires

Dans les cas où le nom de la bibliothèque n’est plus dans la portée, vous pouvez utiliser `__LIBID_` au lieu de **__uuidof**. Par exemple :

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
