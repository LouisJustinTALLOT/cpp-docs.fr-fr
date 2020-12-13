---
description: 'En savoir plus sur : erreur irrécupérable C1308'
title: Erreur irrécupérable C1308
ms.date: 11/04/2016
f1_keywords:
- C1308
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
ms.openlocfilehash: 9d9b8cee128b9ed830c4ba3651ee609d91d42eac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177872"
---
# <a name="fatal-error-c1308"></a>Erreur irrécupérable C1308

la liaison des assemblys n’est pas prise en charge

Un. netmodule est autorisé comme entrée de l’éditeur de liens, mais pas un assembly. Cette erreur peut être générée lorsqu’une tentative est faite pour lier un assembly compilé avec `/clr:safe` .

Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).

L’exemple suivant génère l’C1308 :

```cpp
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

Et puis

```cpp
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```
