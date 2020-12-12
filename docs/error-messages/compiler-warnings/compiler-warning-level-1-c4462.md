---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4462'
title: Avertissement du compilateur (niveau 1) C4462
ms.date: 10/25/2017
f1_keywords:
- C4462
helpviewer_keywords:
- C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
ms.openlocfilehash: 81696df228b2cbe6278521f602d2a6f986cacb13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212530"
---
# <a name="compiler-warning-level-1-c4462"></a>Avertissement du compilateur (niveau 1) C4462

> impossible de déterminer le GUID du type. Le programme risque d'échouer au moment de l'exécution.

L’avertissement C4462 se produit dans une application ou un composant Windows Runtime lorsqu’un `TypedEventHandler` public a parmi l’un de ses paramètres de type une référence à une classe englobante.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md). Par exemple, pour faire de C4462 dans un numéro d’avertissement de niveau 4, ajoutez la ligne suivante à votre fichier de code source :

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>Exemple

Cet exemple génère un avertissement C4462 :

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
