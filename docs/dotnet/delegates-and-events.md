---
title: Delegates and Events | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __event keyword [C++]
- delegate keyword [C++]
- delegates [C++], upgrading from Managed Extensions for C++
- __delegate keyword
- events [C++], upgrading from Managed Extensions for C++
- event keyword [C++]
ms.assetid: 3505c626-7e5f-4492-a947-0e2248f7b84a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 26b67cdce8d52cba7d02f182f0582e20d0303c33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373280"
---
# <a name="delegates-and-events"></a>Délégués et événements

La manière de déclarer des délégués et des événements a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

Double trait de soulignement n’est plus nécessaire, comme indiqué dans l’exemple suivant. Voici un exemple de code dans les Extensions managées :

```
__delegate void ClickEventHandler(int, double);
__delegate void DblClickEventHandler(String*);

__gc class EventSource {
   __event ClickEventHandler* OnClick;
   __event DblClickEventHandler* OnDblClick;
};
```

Le même code dans la nouvelle syntaxe se présente comme suit :

```
delegate void ClickEventHandler( int, double );
delegate void DblClickEventHandler( String^ );

ref class EventSource {
   event ClickEventHandler^ OnClick;
   event DblClickEventHandler^ OnDblClick;
};
```

Événements (et les délégués) sont des types référence, qui est clairement dans la nouvelle syntaxe en raison de l’utilisation du chapeau (`^`).  Événements prennent en charge une syntaxe de déclaration explicite et la forme simple illustrée dans le code précédent. Dans le formulaire explicit, l’utilisateur spécifie le `add`, `raise`, et `remove` méthodes associées à l’événement. (Uniquement la `add` et `remove` méthodes sont requises ; la `raise` est facultative.)

Sous Extensions managées, si vous fournissez ces méthodes, vous ne fournissez pas également une déclaration d’événement explicite, mais vous devez choisir un nom pour l’événement qui n’est pas présent. Chaque méthode est spécifiée sous la forme `add_EventName`, `raise_EventName`, et `remove_EventName`, comme dans l’exemple suivant extrait à partir de la spécification d’Extensions managées :

```
// explicit implementations of add, remove, raise
public __delegate void f(int);
public __gc struct E {
   f* _E;
public:
   E() { _E = 0; }

   __event void add_E1(f* d) { _E += d; }

   static void Go() {
      E* pE = new E;
      pE->E1 += new f(pE, &E::handler);
      pE->E1(17);
      pE->E1 -= new f(pE, &E::handler);
      pE->E1(17);
   }

private:
   __event void raise_E1(int i) {
      if (_E)
         _E(i);
   }

protected:
   __event void remove_E1(f* d) {
      _E -= d;
   }
};
```

La nouvelle syntaxe simplifie la déclaration, comme le montre la traduction suivante. Un événement spécifie les deux ou trois méthodes entourées par des accolades et placé immédiatement après la déclaration de l’événement et son type délégué associé, comme illustré ici :

```
public delegate void f( int );
public ref struct E {
private:
   f^ _E; // delegates are also reference types

public:
   E() {  // note the replacement of 0 with nullptr!
      _E = nullptr;
   }

   // the new aggregate syntax of an explicit event declaration
   event f^ E1 {
   public:
      void add( f^ d ) {
         _E += d;
      }

   protected:
      void remove( f^ d ) {
         _E -= d;
      }

   private:
      void raise( int i ) {
         if ( _E )
            _E( i );
      }
   }

   static void Go() {
      E^ pE = gcnew E;
      pE->E1 += gcnew f( pE, &E::handler );
      pE->E1( 17 );
      pE->E1 -= gcnew f( pE, &E::handler );
      pE->E1( 17 );
   }
};
```

## <a name="see-also"></a>Voir aussi

[Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[delegate (extensions du composant C++)](../windows/delegate-cpp-component-extensions.md)<br/>
[event](../windows/event-cpp-component-extensions.md)