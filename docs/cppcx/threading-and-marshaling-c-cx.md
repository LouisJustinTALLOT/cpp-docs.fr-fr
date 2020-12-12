---
description: 'En savoir plus sur : Threading et marshaling (C++/CX)'
title: Thread et Marshaling (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 7ec045b4023e7c27ef55242af44e64033d40f056
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307598"
---
# <a name="threading-and-marshaling-ccx"></a>Thread et Marshaling (C++/CX)

Dans la grande majorité des cas, les instances de Windows Runtime classes, telles que les objets C++ standard, sont accessibles à partir de n’importe quel thread. Ce type de classe est appelé « agile ». Toutefois, un petit nombre de Windows Runtime classes fournies avec Windows sont non agiles et doit être consommé plus comme les objets COM que les objets C++ standard. Vous n'avez pas besoin d'être un spécialiste en COM pour utiliser les classes non agiles, mais vous devez impérativement prendre en compte le modèle de thread de la classe et son comportement de marshaling. Cet article fournit des informations générales et des conseils pour les rares scénarios dans lesquels vous devez utiliser une instance d'une classe non agile.

## <a name="threading-model-and-marshaling-behavior"></a>Modèle de thread et comportement de marshaling

Une classe Windows Runtime peut prendre en charge l’accès simultané aux threads de différentes façons, comme indiqué par deux attributs qui lui sont appliqués :

- L'attribut`ThreadingModel` peut avoir l'une des valeurs STA, MTA ou Both, définies par l'énumération `ThreadingModel` .

- L'attribut`MarshallingBehavior` peut avoir l'une des valeurs Agile, None ou Standard, définies par l'énumération `MarshallingType` .

L'attribut `ThreadingModel` indique l'emplacement où la classe est chargée lorsqu'elle est activée : uniquement dans un contexte de thread d'interface utilisateur (STA), uniquement dans un contexte de thread d'arrière-plan (MTA) ou dans le contexte du thread ayant créé l'objet (Both). Les valeurs de l'attribut `MarshallingBehavior` font référence à la manière dont l'objet se comporte dans les différents contextes de thread. Dans la plupart des cas, vous n'avez pas besoin de comprendre ces valeurs en détail.  Parmi les classes fournies par l'API Windows, environ 90 % ont `ThreadingModel`=Both et `MarshallingType`=Agile. Cela signifie qu'elles peuvent gérer les détails des threads de bas niveau de façon transparente et efficace.   Lorsque vous utilisez `ref new` pour créer une classe agile, vous pouvez appeler des méthodes sur celle-ci depuis votre thread d'application principal ou un ou plusieurs threads de travail.  En d'autres termes, vous pouvez utiliser une classe agile depuis tout emplacement de votre code, qu'elle soit fournie par Windows ou par une bibliothèque tierce. Il n'est pas nécessaire de vous soucier du modèle de thread de la classe ou du comportement de marshaling.

## <a name="consuming-windows-runtime-components"></a>Utilisation des composants de Windows Runtime

Lorsque vous créez une application plateforme Windows universelle, vous pouvez interagir avec des composants agiles et non agiles. Lorsque vous interagissez avec les composants non agiles, vous pouvez rencontrer l'avertissement suivant :

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Avertissement du compilateur C4451 lors de la consommation de classes non agiles

Pour différentes raisons, certaines classes ne peuvent pas être agiles. Si vous accédez à des instances de classes non agiles depuis un thread d'interface utilisateur et un thread d'arrière-plan, vérifiez avec le plus grand soin que le comportement est correct au moment de l'exécution. Le compilateur Microsoft C++ émet des avertissements quand vous instanciez une classe d’exécution non agile dans votre application au niveau de la portée globale ou que vous déclarez un type non agile comme membre de classe dans une classe ref qui lui-même est marquée comme agile.

Parmi les classes non agiles, les plus faciles à gérer sont celles qui ont `ThreadingModel`=Both et `MarshallingType`=Standard.  Pour rendre ces classes agiles, il suffit d'utiliser la classe d'assistance `Agile<T>` .   L'exemple ci-dessous montre une déclaration d'un objet non agile de type `Windows::Security::Credentials::UI::CredentialPickerOptions^`et l'avertissement du compilateur qui est alors émis.

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

Voici l'avertissement émis :

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Lorsque vous ajoutez une référence, au niveau de portée du membre ou au niveau de portée globale, à un objet qui a un comportement de marshaling Standard, le compilateur émet un avertissement qui vous indique d'encapsuler le type dans `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Si vous utilisez `Agile<T>`, vous pouvez consommer la classe comme avec toute autre classe agile. Utilisez `Platform::Agile<T>` dans les circonstances ci-dessous.

- La variable non agile est déclarée au niveau de la portée globale.

- La variable non agile est déclarée au niveau de la portée d'une classe et la consommation du code peut faire passer en douce le pointeur, c'est-à-dire l'utiliser dans un apartment différent sans marshaling correct.

Si aucune de ces conditions ne s'applique, vous pouvez marquer la classe conteneur comme non agile. En d’autres termes, vous devez directement conserver des objets non agiles uniquement dans des classes non agiles et conserver des objets non agiles via Platform :: Agile \<T> dans les classes agile.

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

Notez que `Agile` ne peut pas être passée comme valeur ou paramètre de retour dans une classe ref. La méthode `Agile<T>::Get()` retourne un handle-to-object (^) que vous pouvez passer à travers l'interface binaire d'application (ABI) dans une méthode ou une propriété publique.

Quand vous créez une référence à une classe in-proc Windows Runtime qui a un comportement de marshaling « None », le compilateur émet un avertissement C4451, mais ne suggère pas d’utiliser `Platform::Agile<T>` .  Le compilateur ne peut apporter aucune aide autre que cet avertissement. Il vous incombe donc d'utiliser la classe correctement et de garantir que votre code n'appelle les composants STA que dans le thread d'interface utilisateur et le composant MTA que dans un thread d'arrière-plan.

## <a name="authoring-agile-windows-runtime-components"></a>Création de composants de Windows Runtime agile

Lorsque vous définissez une classe ref dans C++/CX, elle est agile par défaut (autrement dit, elle a `ThreadingModel` = both et `MarshallingType` = agile).  Si vous utilisez la bibliothèque de modèles C++ Windows Runtime, vous pouvez rendre votre classe agile en dérivant de `FtmBase` , qui utilise `FreeThreadedMarshaller` .  Si vous créez une classe avec `ThreadingModel`=Both ou `ThreadingModel`=MTA, assurez-vous qu'elle est thread-safe.

Vous pouvez modifier le modèle de thread et le comportement de marshaling d'une classe ref. Toutefois, si vous apportez des modifications qui rendent la classe non agile, vous devez connaître les implications associées à ces modifications.

L’exemple suivant montre comment appliquer les `MarshalingBehavior` `ThreadingModel` attributs et à une classe d’exécution dans une bibliothèque de classes Windows Runtime. Lorsqu'une application utilise la DLL et emploie le mot clé `ref new` pour activer un objet de classe `MySTAClass` , l'objet est activé dans un thread cloisonné et ne prend pas en charge le marshaling.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Une classe déverrouillée doit avoir des paramètres d'attribut de marshaling et de thread pour permettre au compilateur de vérifier que les classes dérivées ont la même valeur pour ces attributs. Si ces paramètres ne sont pas définis de manière explicite dans la classe, le compilateur génère une erreur et ne compile pas. Toute classe dérivée d'une classe déverrouillée génère une erreur de compilation dans tous les cas ci-dessous :

- Les attributs `ThreadingModel` et `MarshallingBehavior` ne sont pas définis dans la classe dérivée.

- Les valeurs des attributs `ThreadingModel` et `MarshallingBehavior` dans la classe dérivée ne correspondent pas à celles définies dans la classe de base.

Les informations de Threading et de marshaling requises par un composant Windows Runtime tiers sont spécifiées dans les informations d’inscription du manifeste de l’application pour le composant. Nous vous recommandons de rendre tous vos composants de Windows Runtime agiles. Ainsi, le code client peut appeler votre composant dans n'importe quel thread de l'application et les performances des appels sont améliorées car ce sont des appels directs qui n'ont aucun marshaling. Si vous créez votre classe de cette manière, le code client n'a pas besoin d'utiliser `Platform::Agile<T>` pour consommer votre classe.

## <a name="see-also"></a>Voir aussi

[ThreadingModel](/uwp/api/windows.foundation.metadata.threadingmodel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
