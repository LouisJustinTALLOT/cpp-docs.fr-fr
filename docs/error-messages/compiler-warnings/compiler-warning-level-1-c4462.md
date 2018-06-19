---
title: Compilateur avertissement (niveau 1) C4462 | Documents Microsoft
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4462
dev_langs:
- C++
helpviewer_keywords:
- C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 105a78fe9f8a8d2b6442c9b403af0266de53d3b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281399"
---
# <a name="compiler-warning-level-1-c4462"></a>Avertissement du compilateur (niveau 1) C4462

> impossible de déterminer le GUID du type. Le programme risque d'échouer au moment de l'exécution.

L'avertissement C4462 se produit dans une application ou un composant Windows Runtime lorsqu'un `TypedEventHandler` public a parmi l'un de ses paramètres de type une référence à une classe englobante.

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md). Par exemple, pour que C4462 un niveau 4 avertissement, ajoutez cette ligne à votre fichier de code source :

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>Exemple

Cet exemple génère l’avertissement C4462 :

```cpp
namespace N
{
       public ref struct EventArgs sealed {};
       public ref struct R sealed
       {
              R() {}
              event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
       };
}

[Platform::MTAThread]
int main()
{
     auto x = ref new N::R();
}
```

Il existe deux solutions pour contourner l'erreur. La première solution, comme le montre l'exemple suivant, consiste à donner à l'événement une accessibilité interne afin qu'il soit accessible au code du même exécutable mais pas au code des autres composants Windows Runtime.

```cpp
internal:
    event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
```

Si l'événement doit être public, vous pouvez utiliser l'autre solution, qui consiste à l'exposer via une interface par défaut :

```cpp
ref struct R;
public interface struct IR{ event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;};

public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR
{
    R() {}
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
};
```

Un GUID de type `Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` est utilisé uniquement lorsque le type est accessible à partir d'un autre composant. La première solution fonctionne, car l'événement n'est accessible que dans son propre composant (une fois la solution appliquée). Sinon, le compilateur doit partir du cas le plus défavorable et émettre l'avertissement.
