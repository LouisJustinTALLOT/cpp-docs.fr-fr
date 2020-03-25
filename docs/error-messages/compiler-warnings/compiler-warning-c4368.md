---
title: Avertissement du compilateur C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: d96ae14bc427568dcf7ba7bc6e5d53f3d28883ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165300"
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
