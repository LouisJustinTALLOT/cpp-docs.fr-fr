---
title: événements (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event
- event_cpp
dev_langs:
- C++
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7859b8b58bbd8765c38daea46efea5859ba61d67
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881209"
---
# <a name="event--c-component-extensions"></a>événement  (extensions du composant C++)
Le `event` mot clé déclare une *événement*, qui est une notification aux abonnés inscrits (*gestionnaires d’événements*) qu’un élément d’intérêt s’est produit.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 C + c++ / CX prend en charge la déclaration d’un *membre d’événement* ou *bloc d’événement*. Un membre d'événement est un raccourci pour déclarer un bloc d'événement. Par défaut, un membre d'événement déclare les fonctions `add()`, `remove()` et `raise()` qui sont déclarées explicitement dans un bloc d'événement. Pour personnaliser les fonctions dans un membre d'événement, déclarez un bloc d'événement à la place, puis remplacez les fonctions dont vous avez besoin.  
  
 **Syntaxe**  
  
```  
  
// event data member  
modifiereventdelegate^ event_name;     
  
// event block  
modifiereventdelegate^ event_name   
{  
   modifierreturn_valueadd(delegate^ name);  
   modifier void remove(delegate^ name);  
   modifier void raise(parameters);  
}  
```  
  
 **Paramètres**  
  
 *Modificateur*  
 Modificateur qui peut être utilisé sur la déclaration event ou une méthode d’accesseur d’événement.  Les valeurs possibles sont `static` et `virtual`.  
  
 *delegate*  
 Le [déléguer](../windows/delegate-cpp-component-extensions.md), dont le Gestionnaire d’événements doit correspondre à la signature.  
  
 *Nom_événement*  
 Nom de l'événement.  
  
 *return_value*  
 Valeur de retour de la méthode d’accesseur d’événement.  Pour être vérifiable, le type de retour doit être `void`.  
  
 *Paramètres*  
 (facultatif) Paramètres pour le `raise` (méthode), qui correspond à la signature de la *déléguer* paramètre.  
  
 **Remarques**  
  
 Un événement est une association entre un délégué et une fonction membre (gestionnaire d’événements) qui répond au déclenchement de l’événement et permet aux clients de toute classe d’inscrire des méthodes conformes à la signature et au type de retour du délégué sous-jacent.  
  
 Il existe deux types de déclarations d'événements :  
  
 *membre de données d’événement*  
 Le compilateur crée automatiquement le stockage de l'événement sous la forme d'un membre du type délégué et crée des fonctions membres `add()`, `remove()` et `raise()` internes. Un membre de données d'événement doit être déclaré à l'intérieur d'une classe. Le type de retour du délégué doit correspondre à celui du gestionnaire d’événements.  
  
 *bloc d’événement*  
 Un bloc d'événement vous permet de déclarer et personnaliser explicitement le comportement des méthodes `add()`, `remove()` et `raise()`.  
  
 Vous pouvez utiliser `operators+=` et `operator-=` pour ajouter et supprimer un gestionnaire d'événements ou appeler les méthodes `add()` et `remove()` explicitement.  
  
 `event` est un mot clé contextuel ; consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md) pour plus d’informations.  
  
## <a name="windows-runtime"></a>Windows Runtime  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [événements (C + c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh755799.aspx).  
  
 Si vous envisagez d'ajouter, puis de supprimer un gestionnaire d'événements, vous devez enregistrer la structure EventRegistrationToken retournée par l'opération d'ajout. Ensuite, dans l'opération de suppression, vous devez utiliser la structure EventRegistrationToken enregistrée pour identifier le gestionnaire d'événements à supprimer.  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 Le mot clé `event` vous permet de déclarer un événement. Un événement est un moyen pour une classe de fournir des notifications quand un fait digne d'intérêt se produit.  
  
 **Syntaxe**  
  
```  
  
// event data member  
modifiereventdelegate^ event_name;   
  
// event block  
modifiereventdelegate^ event_name   
{  
   modifierreturn_valueadd(delegate^ name);  
   modifier void remove(delegate^ name);  
   modifier void raise(parameters);  
}  
```  
  
 **Paramètres**  
  
 *Modificateur*  
 Modificateur qui peut être utilisé sur la déclaration event ou une méthode d’accesseur d’événement.  Les valeurs possibles sont `static` et `virtual`.  
  
 *delegate*  
 Le [déléguer](../windows/delegate-cpp-component-extensions.md), dont le Gestionnaire d’événements doit correspondre à la signature.  
  
 *Nom_événement*  
 Nom de l'événement.  
  
 *return_value*  
 Valeur de retour de la méthode d’accesseur d’événement.  Pour être vérifiable, le type de retour doit être `void`.  
  
 *Paramètres*  
 (facultatif) Paramètres pour le `raise` (méthode), qui correspond à la signature de la *déléguer* paramètre.  
  
 **Remarques**  
  
 Un événement est une association entre un délégué et une fonction membre (gestionnaire d’événements) qui répond au déclenchement de l’événement et permet aux clients de toute classe d’inscrire des méthodes conformes à la signature et au type de retour du délégué sous-jacent.  
  
 Le délégué peut avoir une ou plusieurs méthodes associées qui sont appelées quand votre code indique que l'événement s'est produit. Un événement propre à un programme peut être accessible à d'autres programmes qui ciblent le Common Language Runtime du .NET Framework.  
  
 Il existe deux types de déclarations d'événements :  
  
 *membres de données d’événement*  
 Le stockage de l'événement, sous la forme d'un membre du type délégué, est créé par le compilateur pour les événements de membre de données.  Un membre de données d'événement doit être déclaré à l'intérieur d'une classe. Cet événement est également connu sous le nom d'événement trivial (consultez l'exemple de code ci-dessous).  
  
 *blocs d’événement*  
 Les blocs d'événement vous permettent de personnaliser le comportement des méthodes add, remove et raise, en implémentant ces méthodes. La signature des méthodes add, remove et raise doivent correspondre à la signature du délégué.  Les événements de bloc d'événement ne sont pas membres de données et toute utilisation en tant que membre de données génère une erreur du compilateur. 
  
 Le type de retour du gestionnaire d’événements doit correspondre à celui du délégué.  
  
 Dans .NET Framework, vous pouvez traiter un membre de données comme s'il s'agissait d'une méthode (autrement dit, la méthode `Invoke` de son délégué correspondant). Vous devez prédéfinir le type délégué pour déclarer un membre de données d'événement managé. En revanche, une méthode d'événement managé définit implicitement le délégué managé correspondant, s'il n'est pas déjà défini.  Consultez l'exemple de code fourni à la fin de cette rubrique pour obtenir un exemple.  
  
 Lors de la déclaration d'un événement managé, vous pouvez spécifier des accesseurs add et remove qui sont appelés quand les gestionnaires d'événements sont ajoutés ou supprimés à l'aide des opérateurs += et -=. Les méthodes add, remove et raise peuvent être appelées explicitement.  
  
 Les étapes suivantes doivent être suivies pour créer et utiliser des événements en Visual C++ :  
  
1.  Créez ou identifiez un délégué. Si vous définissez votre propre événement, vous devez également vous assurer qu'il existe un délégué à utiliser avec le mot clé `event`. Si l'événement est prédéfini, dans le .NET Framework par exemple, alors les consommateurs de l'événement doivent uniquement connaître le nom du délégué.  
  
2.  Créez une classe qui contient :  
  
    -   Un événement créé à partir du délégué.  
  
    -   (facultatif) Une méthode qui vérifie qu'une instance du délégué déclaré avec le mot clé `event` existe. Sinon, cette logique doit être placée dans le code qui déclenche l'événement.  
  
    -   Des méthodes qui appellent l'événement. Ces méthodes peuvent être des substitutions de certaines fonctionnalités de la classe de base.  
  
     Cette classe définit l'événement.  
  
3.  Définissez une ou plusieurs classes qui connectent les méthodes à l'événement. Chacune de ces classes associe une ou plusieurs méthodes à l'événement dans la classe de base.  
  
4.  Utilisez l'événement :  
  
    -   Créez un objet de la classe qui contient la déclaration de l'événement.  
  
    -   Créez un objet de la classe qui contient la déclaration de l'événement.  
  
 Pour plus d’informations sur le langage c++ / CLI, événements, consultez  
  
-   [Événements dans une Interface](../dotnet/how-to-use-events-in-cpp-cli.md)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 L'exemple de code suivant illustre : la déclaration de paires de délégués, d'événements et de gestionnaires d'événements, l'abonnement (ajout) des gestionnaires d'événements, l'appel des gestionnaires d'événements, puis l'annulation de l'abonnement (suppression) des gestionnaires d'événements.  
  
```  
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
  
 **Sortie**  
  
```Output  
OnClick: 7, 3.14159  
  
OnDblClick: Hello  
```  
  
 **Exemple**  
  
 L'exemple de code suivant illustre la logique utilisée pour générer la méthode `raise` d'un événement trivial : si l'événement a un ou plusieurs abonnés, l'appel à la méthode `raise` permet d'appeler implicitement ou explicitement le délégué. Si le type de retour du délégué n'est pas `void` et que le nombre d'abonnés à l'événement s'élève à zéro, la méthode `raise` retourne la valeur par défaut pour le type délégué. En l'absence d'abonnés à l'événement, l'appel à la méthode `raise` entraîne un retour simple et aucune exception n'est levée. Si le type de retour du délégué n'est pas `void`, le type délégué est retourné.  
  
```  
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
  
 **Sortie**  
  
```Output  
0  
  
688  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)