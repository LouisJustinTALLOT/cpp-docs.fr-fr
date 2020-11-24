---
title: Event, mot clé (C++/CLI et C++/CX)
description: Découvrez comment utiliser le mot clé Microsoft C++ Component extensions `event` .
ms.date: 11/20/2020
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.openlocfilehash: 6a2fa97140f747b4afc380b57f8f7c71f08875db
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483241"
---
# <a name="event-keyword-ccli-and-ccx"></a>`event` mot clé (C++/CLI et C++/CX)

Le **`event`** mot clé déclare un *événement*, qui est une notification aux abonnés inscrits (*gestionnaires d’événements*) qu’une chose d’intérêt s’est produite.

## <a name="all-runtimes"></a>Tous les runtimes

C++/CX prend en charge la déclaration d’un *membre d’événement* ou d’un *bloc d’événement*. Un membre d'événement est un raccourci pour déclarer un bloc d'événement. Par défaut, un membre d'événement déclare les fonctions `add`, `remove` et `raise` qui sont déclarées explicitement dans un bloc d'événement. Pour personnaliser les fonctions dans un membre d'événement, déclarez un bloc d'événement à la place, puis remplacez les fonctions dont vous avez besoin.

### <a name="syntax"></a>Syntaxe

```cpp
// event data member
modifier event delegate^ event_name;

// event block
modifier event delegate^ event_name
{
   modifier return_value add(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Paramètres

*modificateur*\
Modificateur qui peut être utilisé sur la déclaration event ou une méthode d’accesseur d’événement.  Les valeurs possibles sont **`static`** et **`virtual`** .

*disposer*\
[Délégué](delegate-cpp-component-extensions.md) dont la signature doit correspondre au gestionnaire d’événements.

*event_name*\
Nom de l’événement.

*return_value*\
Valeur de retour de la méthode d’accesseur d’événement.  Pour être vérifiable, le type de retour doit être **`void`** .

*paramètres*\
(facultatif) Paramètres de la méthode `raise`, qui correspondent à la signature du paramètre *delegate*.

### <a name="remarks"></a>Notes

Un événement est une association entre un délégué et un *Gestionnaire d’événements*. Un gestionnaire d’événements est une fonction membre qui répond quand l’événement est déclenché. Elle permet aux clients de n’importe quelle classe d’inscrire des méthodes qui correspondent à la signature et au type de retour du délégué.

Il existe deux types de déclarations d'événements :

*membre de données d’événement*\
Le compilateur crée automatiquement le stockage de l'événement sous la forme d'un membre du type délégué et crée des fonctions membres `add`, `remove` et `raise` internes. Un membre de données d'événement doit être déclaré à l'intérieur d'une classe. Le type de retour du délégué doit correspondre à celui du gestionnaire d'événements.

*bloc d’événements*\
Un bloc d'événement vous permet de déclarer et personnaliser explicitement le comportement des méthodes `add`, `remove` et `raise`.

Vous pouvez utiliser `operator +=` et `operator -=` pour ajouter et supprimer un gestionnaire d’événements, ou appeler `add` les `remove` méthodes et explicitement.

**`event`** est un mot clé contextuel. Pour plus d’informations, consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Événements (C++/CX)](../cppcx/events-c-cx.md).

Pour ajouter et supprimer ultérieurement un gestionnaire d’événements, enregistrez la `EventRegistrationToken` structure retournée par l' `add` opération. Ensuite, dans l' `remove` opération, utilisez la `EventRegistrationToken` structure enregistrée pour identifier le gestionnaire d’événements à supprimer.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Le mot clé **event** vous permet de déclarer un événement. Un événement est un moyen pour une classe de fournir des notifications quand un fait digne d'intérêt se produit.

### <a name="syntax"></a>Syntaxe

```cpp
// event data member
modifier event delegate^ event_name;

// event block
modifier event delegate^ event_name
{
   modifier return_value add(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Paramètres

*modificateur*\
Modificateur qui peut être utilisé sur la déclaration event ou une méthode d’accesseur d’événement.  Les valeurs possibles sont **`static`** et **`virtual`** .

*disposer*\
[Délégué](delegate-cpp-component-extensions.md) dont la signature doit correspondre au gestionnaire d’événements.

*event_name*\
Nom de l’événement.

*return_value*\
Valeur de retour de la méthode d’accesseur d’événement.  Pour être vérifiable, le type de retour doit être **`void`** .

*paramètres*\
(facultatif) Paramètres de la méthode `raise`, qui correspondent à la signature du paramètre *delegate*.

### <a name="remarks"></a>Notes

Un événement est une association entre un délégué et un *Gestionnaire d’événements*. Un gestionnaire d’événements est une fonction membre qui répond quand l’événement est déclenché. Elle permet aux clients de n’importe quelle classe d’inscrire des méthodes qui correspondent à la signature et au type de retour du délégué sous-jacent.

Le délégué peut avoir une ou plusieurs méthodes associées. Ces méthodes sont appelées lorsque votre code indique que l’événement s’est produit. Un événement propre à un programme peut être accessible à d'autres programmes qui ciblent le Common Language Runtime du .NET Framework.

Il existe deux types de déclarations d’événements :

*membres de données d’événement*\
Le compilateur crée un stockage pour les événements de membre de données en tant que membre du type délégué. Un membre de données d'événement doit être déclaré à l'intérieur d'une classe. Il est également connu sous le nom d' *événement trivial*. Pour obtenir un exemple, consultez l’exemple de code.

*blocs d’événements*\
Les blocs d’événements vous permettent de personnaliser le comportement des `add` `remove` méthodes, et `raise` , en implémentant les `add` méthodes, `remove` et `raise` . La signature des `add` méthodes, `remove` et `raise` doit correspondre à la signature du délégué. Les événements de bloc d’événements ne sont pas des membres de données. Toute utilisation en tant que membre de données génère une erreur du compilateur.

Le type de retour du gestionnaire d'événements doit correspondre à celui du délégué.

Dans .NET Framework, vous pouvez traiter un membre de données comme s'il s'agissait d'une méthode (autrement dit, la méthode `Invoke` de son délégué correspondant). Pour ce faire, prédéfinissez le type délégué pour la déclaration d’un membre de données d’événement managé. En revanche, une méthode d’événement managé définit implicitement le délégué managé correspondant s’il n’est pas déjà défini. Pour obtenir un exemple, consultez l’exemple de code à la fin de cet article.

Lors de la déclaration d’un événement managé, vous pouvez spécifier `add` les `remove` accesseurs et qui seront appelés lorsque les gestionnaires d’événements sont ajoutés ou supprimés à l’aide **`+=`** des opérateurs et **`-=`** . Les `add` `remove` méthodes, et `raise` peuvent être appelées explicitement.

Les étapes suivantes doivent être effectuées pour créer et utiliser des événements dans Microsoft C++ :

1. Créez ou identifiez un délégué. Si vous définissez votre propre événement, vous devez également vous assurer qu’il existe un délégué à utiliser avec le **`event`** mot clé. Si l'événement est prédéfini, dans le .NET Framework par exemple, alors les consommateurs de l'événement doivent uniquement connaître le nom du délégué.

2. Créez une classe qui contient :

   - Un événement créé à partir du délégué.

   - Facultatif Méthode qui vérifie qu’une instance du délégué déclaré avec le **`event`** mot clé existe. Sinon, cette logique doit être placée dans le code qui déclenche l'événement.

   - Des méthodes qui appellent l'événement. Ces méthodes peuvent être des substitutions de certaines fonctionnalités de la classe de base.

   Cette classe définit l'événement.

3. Définissez une ou plusieurs classes qui connectent les méthodes à l'événement. Chacune de ces classes associe une ou plusieurs méthodes à l'événement dans la classe de base.

4. Utilisez l'événement :

   - Créez un objet de la classe qui contient la déclaration de l'événement.

   - Créez un objet de la classe qui contient la déclaration de l'événement.

Pour plus d’informations sur les événements C++/CLI, consultez [événements dans une interface](../dotnet/how-to-use-events-in-cpp-cli.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant illustre la déclaration de paires de délégués, d’événements et de gestionnaires d’événements. Il montre comment s’abonner (ajouter), appeler, puis annuler l’abonnement (supprimer) des gestionnaires d’événements.

```cpp
// mcppv2_events.cpp
// compile with: /clr
using namespace System;

// declare delegates
delegate void ClickEventHandler(int, double);
delegate void DblClickEventHandler(String^);

// class that defines events
ref class EventSource {
public:
   event ClickEventHandler^ OnClick;   // declare the event OnClick
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick

   void FireEvents() {
      // raises events
      OnClick(7, 3.14159);
      OnDblClick("Hello");
   }
};

// class that defines methods that will called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }

   void OnMyDblClick(String^ str) {
      Console::WriteLine("OnDblClick: {0}", str);
   }
};

int main() {
   EventSource ^ MyEventSource = gcnew EventSource();
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);

   // invoke events
   MyEventSource->FireEvents();

   // unhook handler to event
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);
}
```

```Output
OnClick: 7, 3.14159

OnDblClick: Hello
```

L’exemple de code suivant illustre la logique utilisée pour générer la `raise` méthode d’un événement trivial. Si l’événement a un ou plusieurs abonnés, appeler la méthode `raise` implicitement ou explicitement appelle le délégué. Si le type de retour du délégué n’est pas **`void`** et s’il n’y a aucun abonné aux événements, la `raise` méthode retourne la valeur par défaut pour le type délégué. S’il n’y a pas d’abonnés aux événements, l’appel de la `raise` méthode retourne immédiatement et aucune exception n’est levée. Si le type de retour du délégué n’est pas **`void`** , le type délégué est retourné.

```cpp
// trivial_events.cpp
// compile with: /clr /c
using namespace System;
public delegate int Del();
public ref struct C {
   int i;
   event Del^ MyEvent;

   void FireEvent() {
      i = MyEvent();
   }
};

ref struct EventReceiver {
   int OnMyClick() { return 0; }
};

int main() {
   C c;
   c.i = 687;

   c.FireEvent();
   Console::WriteLine(c.i);
   c.i = 688;

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);
   Console::WriteLine(c.i);
}
```

```Output
0

688
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
