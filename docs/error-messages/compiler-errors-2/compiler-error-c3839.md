---
title: Erreur du compilateur C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 19a1055a461d76856cc3bccbd9f8af0f0dcff356
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754925"
---
# <a name="compiler-error-c3839"></a>Erreur du compilateur C3839

impossible de changer l'alignement dans un type managé ou WinRT

L’alignement des variables dans les types managés ou Windows Runtime est contrôlé par le CLR ou Windows Runtime et ne peut pas être modifié avec [align](../../cpp/align-cpp.md).

L'exemple suivant génère l'erreur C3839 :

```cpp
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```
