---
title: "Thread et Marshaling (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4451"
helpviewer_keywords: 
  - "problèmes liés aux threads, C++/CX"
  - "souplesse, C++/CX"
  - "C++/CX, problèmes liés aux threads"
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 17
---
# Thread et Marshaling (C++/CX)
Dans la grande majorité des cas, les instances des classes [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], telles que les objets C\+\+ standard, sont accessibles depuis n'importe quel thread. Ce type de classe est appelé « agile ». Cependant, un petit nombre de classes [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] fournies avec Windows sont non agiles et doivent être utilisés davantage comme des objets COM que comme des objets C\+\+ standard. Vous n'avez pas besoin d'être un spécialiste en COM pour utiliser les classes non agiles, mais vous devez impérativement prendre en compte le modèle de thread de la classe et son comportement de marshaling. Cet article fournit des informations générales et des conseils pour les rares scénarios dans lesquels vous devez utiliser une instance d'une classe non agile.  
  
## Modèle de thread et comportement de marshaling  
 Une classe [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] peut prendre l'accès au thread simultané de différentes manières, comme indiqué par deux attributs qui lui sont appliqués :  
  
-   L'attribut `ThreadingModel` peut avoir l'une des valeurs STA, MTA ou Both, définies par l'énumération `ThreadingModel`.  
  
-   L'attribut `MarshallingBehavior` peut avoir l'une des valeurs Agile, None ou Standard, définies par l'énumération `MarshallingType`.  
  
 L'attribut `ThreadingModel` indique l'emplacement où la classe est chargée lorsqu'elle est activée : uniquement dans un contexte de thread d'interface utilisateur \(STA\), uniquement dans un contexte de thread d'arrière\-plan \(MTA\) ou dans le contexte du thread ayant créé l'objet \(Both\). Les valeurs de l'attribut `MarshallingBehavior` font référence à la manière dont l'objet se comporte dans les différents contextes de thread. Dans la plupart des cas, vous n'avez pas besoin de comprendre ces valeurs en détail.  Parmi les classes fournies par l'API Windows, environ 90 % ont `ThreadingModel`\=Both et `MarshallingType`\=Agile. Cela signifie qu'elles peuvent gérer les détails des threads de bas niveau de façon transparente et efficace.   Lorsque vous utilisez `ref new` pour créer une classe agile, vous pouvez appeler des méthodes sur celle\-ci depuis votre thread d'application principal ou un ou plusieurs threads de travail.  En d'autres termes, vous pouvez utiliser une classe agile depuis tout emplacement de votre code, qu'elle soit fournie par Windows ou par une bibliothèque tierce. Il n'est pas nécessaire de vous soucier du modèle de thread de la classe ou du comportement de marshaling.  
  
## Consommation des composants [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]  
 Lorsque vous créez une application [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], vous pouvez interagir avec des composants agiles et non agiles. Lorsque vous interagissez avec les composants non agiles, vous pouvez rencontrer l'avertissement suivant :  
  
### Avertissement du compilateur lors de la consommation de classes non agiles \(C4451\)  
 Pour différentes raisons, certaines classes ne peuvent pas être agiles. Si vous accédez à des instances de classes non agiles depuis un thread d'interface utilisateur et un thread d'arrière\-plan, vérifiez avec le plus grand soin que le comportement est correct au moment de l'exécution. Le compilateur Visual C\+\+ émet des avertissements lorsque vous instanciez une classe d'exécution non agile dans votre application au niveau de la portée globale ou que vous déclarez un type non agile comme membre de classe d'une classe ref elle\-même marquée comme agile.  
  
 Parmi les classes non agiles, les plus faciles à gérer sont celles qui ont `ThreadingModel`\=Both et `MarshallingType`\=Standard.  Pour rendre ces classes agiles, il suffit d'utiliser la classe d'assistance `Agile<T>`.   L'exemple ci\-dessous montre une déclaration d'un objet non agile de type `Windows::Security::Credentials::UI::CredentialPickerOptions^` et l'avertissement du compilateur qui est alors émis.  
  
```  
  
ref class MyOptions  
    {  
    public:  
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options  
  
        {  
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()   
            {  
                return _myOptions;  
            }  
        }  
    private:  
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;  
    };  
```  
  
 Voici l'avertissement émis :  
  
> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`  
  
 Lorsque vous ajoutez une référence, au niveau de portée du membre ou au niveau de portée globale, à un objet qui a un comportement de marshaling Standard, le compilateur émet un avertissement qui vous indique d'encapsuler le type dans `Platform::Agile<T>` : `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Si vous utilisez `Agile<T>`, vous pouvez consommer la classe comme avec toute autre classe agile. Utilisez `Platform::Agile<T>` dans les circonstances ci\-dessous.  
  
-   La variable non agile est déclarée au niveau de la portée globale.  
  
-   La variable non agile est déclarée au niveau de la portée d'une classe et la consommation du code peut faire passer en douce le pointeur, c'est\-à\-dire l'utiliser dans un apartment différent sans marshaling correct.  
  
 Si aucune de ces conditions ne s'applique, vous pouvez marquer la classe conteneur comme non agile. En d'autres termes, vous devez directement contenir les objets non agiles dans des classes non agiles, ainsi que contenir les objets non agiles via Platform::Agile\<T\> dans les classes agiles.  
  
 L'exemple suivant montre comment utiliser `Agile<T>` afin d'ignorer sans risque l'avertissement.  
  
```  
  
#include <agile.h>  
ref class MyOptions  
    {  
    public:  
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options  
  
        {  
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()   
            {  
                return m_myOptions.Get();  
            }  
        }  
    private:  
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;  
  
    };  
  
```  
  
 Notez que `Agile` ne peut pas être passée comme valeur ou paramètre de retour dans une classe ref. La méthode `Agile<T>::Get()` retourne un handle\-to\-object \(^\) que vous pouvez passer à travers l'interface binaire d'application \(ABI\) dans une méthode ou une propriété publique.  
  
 Dans Visual C\+\+, lorsque vous créez une référence à une classe [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] in\-process qui a un comportement de marshaling None, le compilateur émet un avertissement C4451 mais ne vous propose pas d'utiliser `Platform::Agile<T>`.  Le compilateur ne peut apporter aucune aide autre que cet avertissement. Il vous incombe donc d'utiliser la classe correctement et de garantir que votre code n'appelle les composants STA que dans le thread d'interface utilisateur et le composant MTA que dans un thread d'arrière\-plan.  
  
## Création de composants [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] agiles  
 Lorsque vous définissez une classe ref dans [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], elle est agile par défaut, c'est\-à\-dire qu'elle a `ThreadingModel`\=Both et `MarshallingType`\=Agile.  Si vous utilisez [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)], vous pouvez rendre votre classe agile par une dérivation à partir de `FtmBase`, qui utilise `FreeThreadedMarshaller`.  Si vous créez une classe avec `ThreadingModel`\=Both ou `ThreadingModel`\=MTA, assurez\-vous qu'elle est thread\-safe. Pour plus d’informations, consultez [Créer et consommer des objets \(WRL\)](http://msdn.microsoft.com/fr-fr/d5e42216-e888-4f1f-865a-b5ccd0def73e).  
  
 Vous pouvez modifier le modèle de thread et le comportement de marshaling d'une classe ref. Toutefois, si vous apportez des modifications qui rendent la classe non agile, vous devez connaître les implications associées à ces modifications.  
  
 L'exemple ci\-dessous indique comment appliquer les attributs `MarshalingBehavior` et `ThreadingModel` à une classe d'exécution dans une bibliothèque de classes [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Lorsqu'une application utilise la DLL et emploie le mot clé `ref new` pour activer un objet de classe `MySTAClass`, l'objet est activé dans un thread cloisonné et ne prend pas en charge le marshaling.  
  
```  
using namespace Windows::Foundation::Metadata;  
using namespace Platform;  
  
[Threading(ThreadingModel::STA)]  
[MarshalingBehavior(MarshalingType::None)]   
public ref class MySTAClass  
{  
};  
  
```  
  
 Une classe déverrouillée doit avoir des paramètres d'attribut de marshaling et de thread pour permettre au compilateur de vérifier que les classes dérivées ont la même valeur pour ces attributs. Si ces paramètres ne sont pas définis de manière explicite dans la classe, le compilateur génère une erreur et ne compile pas. Toute classe dérivée d'une classe déverrouillée génère une erreur de compilation dans tous les cas ci\-dessous :  
  
-   Les attributs `ThreadingModel` et `MarshallingBehavior` ne sont pas définis dans la classe dérivée.  
  
-   Les valeurs des attributs `ThreadingModel` et `MarshallingBehavior` dans la classe dérivée ne correspondent pas à celles définies dans la classe de base.  
  
 Les informations de threading et de marshaling requises par un composant [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] tiers sont spécifiées dans le formulaire d'inscription de manifeste d'application du composant. Nous vous recommandons de rendre tous vos composants [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] agiles. Ainsi, le code client peut appeler votre composant dans n'importe quel thread de l'application et les performances des appels sont améliorées car ce sont des appels directs qui n'ont aucun marshaling. Si vous créez votre classe de cette manière, le code client n'a pas besoin d'utiliser `Platform::Agile<T>` pour consommer votre classe.  
  
## Voir aussi  
 [\(NOTINBUILD\) Rubriques avancées](http://msdn.microsoft.com/fr-fr/1ccff0cf-a6cc-47ef-a05f-eba6307b3ced)   
 [ThreadingModel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.threadingmodel.aspx)   
 [MarshallingBehavior](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.marshalingbehaviorattribute.aspx)