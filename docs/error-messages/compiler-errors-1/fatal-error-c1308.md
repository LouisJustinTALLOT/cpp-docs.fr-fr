---
title: Erreur irrécupérable C1308
ms.date: 11/04/2016
f1_keywords:
- C1308
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
ms.openlocfilehash: 0128953b3b3fa0f29a6764c1d7dab0ece67dfae7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640620"
---
# <a name="fatal-error-c1308"></a>Erreur irrécupérable C1308

liaison des assemblys n’est pas pris en charge.

Un fichier .netmodule est autorisé comme entrée dans l’éditeur de liens, mais n’est pas un assembly. Cette erreur peut être générée lorsqu’une tentative est effectuée pour lier un assembly compilé avec `/clr:safe`.

Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).

L’exemple suivant génère l’erreur C1308 :

```
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

Et puis

```
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```