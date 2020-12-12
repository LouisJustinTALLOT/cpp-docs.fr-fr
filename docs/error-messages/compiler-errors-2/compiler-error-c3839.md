---
description: 'En savoir plus sur : erreur du compilateur C3839'
title: Erreur du compilateur C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 8b34cdd7f09bea924d3e184f7ea639c3f8210ed5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180797"
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
