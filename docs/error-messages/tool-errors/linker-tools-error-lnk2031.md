---
title: Erreur des outils Éditeur de liens LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 096ccb7ff443d24e0d53e73a5950faa1e85aeae6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194562"
---
# <a name="linker-tools-error-lnk2031"></a>Erreur des outils Éditeur de liens LNK2031

> Impossible de générer p/Invoke pour «*function_declaration*» *Decorated_Name*; Convention d’appel manquante dans les métadonnées

## <a name="remarks"></a>Notes

Lorsque vous tentez d’importer une fonction native dans une image pure, n’oubliez pas que les conventions d’appel implicites diffèrent entre les compilations native et pure. Pour plus d’informations sur les images pures, consultez [Code pur et vérifiableC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

## <a name="example"></a>Exemple

Cet exemple de code génère un composant avec une fonction exportée, native, dont la Convention d’appel est implicitement [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Exemple

L’exemple suivant crée un client pur qui utilise la fonction native. Toutefois, la Convention d’appel sous **/clr : pure** est [__clrcall](../../cpp/clrcall.md). L’exemple suivant génère l’LNK2031.

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

L’exemple suivant montre comment utiliser la fonction native à partir d’une image pure. Notez le spécificateur de convention d’appel explicite **__cdecl** .

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
