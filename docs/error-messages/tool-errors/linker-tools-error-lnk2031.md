---
title: Erreur des outils Éditeur de liens LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 003b9a58bfb08130f034530f59e2de27efa2ae8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484834"
---
# <a name="linker-tools-error-lnk2031"></a>Erreur des outils Éditeur de liens LNK2031

> Impossible de générer p/invoke pour «*function_declaration*» *nom_décoré*; convention d’appel manquante dans les métadonnées

## <a name="remarks"></a>Notes

Lorsque vous tentez d’importer une fonction native dans une image pure, n’oubliez pas que les conventions d’appel implicites diffèrent entre les compilations natives et pures. Pour plus d’informations sur les images purs, consultez [Code pur et vérifiable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

## <a name="example"></a>Exemple

Cet exemple de code génère un composant avec une fonction exportée native, dont la convention d’appel est implicitement [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Exemple

L’exemple suivant crée un client pur qui utilise la fonction native. Toutefois, la convention d’appel sous **/CLR : pure** est [__clrcall](../../cpp/clrcall.md). L’exemple suivant génère l’erreur LNK2031.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la fonction native à partir d’une image pure. Notez l’explicite **__cdecl** appelant spécificateur de la convention.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```