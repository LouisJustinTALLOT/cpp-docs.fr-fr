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
ms.openlocfilehash: a14ef9043ec2196ff930a37d0eff95e90024d3d5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769197"
---
# <a name="uuidof-operator"></a>__uuidof, opérateur

**Section spécifique à Microsoft**

Récupère le GUID associé à l’expression.

## <a name="syntax"></a>Syntaxe

```
__uuidof (expression)
```

## <a name="remarks"></a>Notes

Le *expression* peut être un nom de type, un pointeur, une référence ou un tableau de ce type, un modèle spécialisé sur ces types, ou une variable de ces types. L’argument est valide tant que le compilateur peut l’utiliser pour rechercher le GUID attaché.

Un cas spécial de cette intrinsèque est lorsque deux **0** ou valeur NULL est fournie comme argument. Dans ce cas, **__uuidof** renverra un GUID composé de zéros non significatifs.

Utilisez ce mot clé pour extraire le GUID attaché à :

- Un objet par le [uuid](../cpp/uuid-cpp.md) attributs étendus.

- Un bloc de bibliothèque est créé avec le [module](../windows/attributes/module-cpp.md) attribut.

> [!NOTE]
> Dans une version debug, **__uuidof** toujours Initialise un objet dynamiquement (lors de l’exécution). Dans une version Release, **__uuidof** peut initialiser statiquement (au moment de la compilation) un objet.

Pour assurer la compatibilité avec les versions précédentes, **_uuidof** est un synonyme de **__uuidof** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

## <a name="example"></a>Exemple

Le code suivant (compilé avec ole32.lib) affiche l’uuid d’un bloc de bibliothèque créé avec l’attribut de module :

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

Dans les cas où le nom de la bibliothèque n’est plus dans la portée, vous pouvez utiliser `__LIBID_` au lieu de **__uuidof**. Exemple :

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)