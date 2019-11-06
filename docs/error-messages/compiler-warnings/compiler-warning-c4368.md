---
title: Avertissement du compilateur C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: b1870d076d21c02574793a8079c4658b39ebf121
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623646"
---
# <a name="compiler-warning-c4368"></a>Avertissement du compilateur C4368

Impossible de définir’Member’en tant que membre de’type’managé : les types mixtes ne sont pas pris en charge

Vous ne pouvez pas incorporer un membre de données natif dans un type CLR.

Toutefois, vous pouvez déclarer un pointeur vers un type natif et contrôler sa durée de vie dans le constructeur et le destructeur et le finaliseur de votre classe managée. Pour plus d’informations [, consultez destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Cet avertissement est toujours émis en tant qu’erreur. Utilisez le pragma [Warning](../../preprocessor/warning.md) pour désactiver C4368.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4368.

```cpp
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```