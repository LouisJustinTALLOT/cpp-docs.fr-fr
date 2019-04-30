---
title: Délégués (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: e2158adad288045c9a98889dbe97e834dc93ea71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406923"
---
# <a name="delegates-ccx"></a>Délégués (C++/CX)

Le `delegate` mot clé est utilisé pour déclarer un type référence qui est l’équivalent Windows Runtime d’un objet de fonction en C++ standard. Une déclaration delegate est similaire à une signature de fonction. Elle spécifie le type de retour et les types de paramètre que sa fonction incluse dans un wrapper doit comporter. Voici une déclaration delegate définie par l'utilisateur :

```cpp
public delegate void PrimeFoundHandler(int result);
```

Les délégués sont plus fréquemment utilisés conjointement avec les événements. Un événement a un type délégué, de la même manière qu'une classe peut avoir un type interface. Le délégué représente un contrat que les gestionnaires d'événements remplissent en grande partie. Voici un membre de classe d'événements dont le type correspond au délégué défini précédemment :

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Lorsque vous déclarez des délégués qui seront exposées aux clients sur l’interface binaire d’application Windows Runtime, utilisez [Windows::Foundation :: typedeventhandler\<TSender, TResult >](/uwp/api/windows.foundation.typedeventhandler). Ce délégué a des binaires stub et proxy prédéfinis qui lui permettent d'être consommé par des clients Javascript.

## <a name="consuming-delegates"></a>Utilisation des délégués

Lorsque vous créez une application de plateforme Windows universelle, vous utilisez souvent un délégué en tant que le type d’événement qui expose une classe Windows Runtime. Pour s'abonner à un événement, créez une instance de son type délégué en spécifiant une fonction (ou lambda) qui correspond à la signature du délégué. Ensuite, utilisez l'opérateur `+=` pour transmettre l'objet délégué au membre d'événement dans la classe. Ce concept est appelé abonnement à l'événement. Lorsque l'instance de classe « déclenche » l'événement, votre fonction est appelée, ainsi que tous les autres gestionnaires ajoutés par votre objet ou d'autres objets.

> [!TIP]
> Visual Studio exécute un volume important de travail lorsque vous créez un gestionnaire d'événements. Par exemple, si vous spécifiez un gestionnaire d'événements dans le balisage XAML, une info-bulle s'affiche. Si vous choisissez l'info-bulle, Visual Studio crée automatiquement la méthode de gestionnaire d'événements et l'associe à l'événement dans la classe d'édition.

L'exemple suivant illustre le modèle de base. `Windows::Foundation::TypedEventHandler` est le type délégué. La fonction gestionnaire est créée à l'aide d'une fonction nommée.

Dans app.h :

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

Dans app.cpp :

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> En général, pour un gestionnaire d'événements, il est préférable d'utiliser une fonction nommée au lieu d'une fonction lambda, à moins que vous ne souhaitiez particulièrement éviter les références circulaires. Une fonction nommée capture le pointeur « this » par une référence faible, mais une fonction lambda le capture par une référence forte et crée une référence circulaire. Pour plus d’informations, consultez [références faibles et cycles de rupture](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Par convention, les noms de délégué de gestionnaire d’événements qui sont définies par l’exécution de Windows ont la forme * EventHandler, par exemple, RoutedEventHandler, SizeChangedEventHandler ou SuspendingEventHandler. Également par convention, les délégués de gestionnaire d'événements ont deux paramètres et retournent la valeur void. Dans un délégué sans paramètres de type, le premier paramètre est de type [Platform::Object^](../cppcx/platform-object-class.md); il contient une référence à l'expéditeur, qui est l'objet qui a déclenché l'événement. Vous devez effectuer un cast vers le type d'origine avant d'utiliser la méthode de gestionnaire d'argument d'événement. Dans un délégué de gestionnaire d'événements ayant des paramètres de type, le premier paramètre de type spécifie le type de l'expéditeur et le deuxième paramètre est un handle à une classe de référence qui contient des informations sur l'événement. Par convention, cette classe est nommée \*EventArgs. Par exemple, un délégué RoutedEventHandler est doté d'un deuxième paramètre de type RoutedEventArgs^, et DragEventHander d'un deuxième paramètre de type DragEventArgs^.

Par convention, les délégués qui encapsulent le code exécuté lorsqu'une opération asynchrone se termine sont nommés *CompletedHandler. Ces délégués sont définis comme propriétés sur la classe, et non en tant qu'événements. De ce fait, n'utilisez pas l'opérateur `+=` pour vous y abonner ; n'assignez qu'un seul objet délégué à la propriété.

> [!TIP]
> C++ IntelliSense n'affiche pas la signature du délégué complète ; par conséquent, il ne vous permet pas de déterminer le type spécifique du paramètre EventArgs. Pour rechercher le type, vous pouvez accéder à l' **Explorateur d'objets** et consulter la méthode `Invoke` pour le délégué.

## <a name="creating-custom-delegates"></a>Création des délégués personnalisés

Vous pouvez définir vos propres délégués, pour définir des gestionnaires d’événements ou pour permettre aux consommateurs de passer des fonctionnalités personnalisées à votre composant Windows Runtime. Comme tout autre type Windows Runtime, un délégué public ne peut pas être déclaré comme générique.

### <a name="declaration"></a>Déclaration

La déclaration d'un délégué ressemble à une déclaration de fonction sauf que le délégué est un type. En général, vous déclarez un délégué à la portée d'espace de noms, même si vous pouvez également imbriquer une déclaration de délégué au sein d'une déclaration de classe. Le délégué suivant encapsule une fonction qui prend un `ContactInfo^` comme entrée et retourne `Platform::String^`.

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Une fois que vous déclarez un type délégué, vous pouvez déclarer des membres de la classe de ce type ou des méthodes qui prennent des objets de ce type en tant que paramètres. Une méthode ou une fonction peut également retourner un type délégué. Dans l'exemple suivant, la méthode `ToCustomString` prend le délégué comme paramètre d'entrée. La méthode permet à un code client de fournir une fonction personnalisée qui construit une chaîne à l'aide d'une partie ou de toutes les propriétés publiques d'un objet `ContactInfo` .

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Vous utilisez le « ^ » de symboles lorsque vous faites référence au type délégué, tout comme vous avec n’importe quel Runtime Windows type référence.

Une déclaration d'événement a toujours un type délégué. Cet exemple montre un délégué classique signature de type dans le Runtime de Windows :

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

L'événement `Click` de la classe `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` est de type `RoutedEventHandler`. Pour plus d'informations, consultez [Events](../cppcx/events-c-cx.md).

Le code client construit d'abord l'instance de délégué en utilisant `ref new` et en fournissant une valeur lambda qui est compatible avec la signature du délégué et définit le comportement personnalisé.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Il appelle ensuite la fonction membre et passe le délégué. Supposons que `ci` est une instance de `ContactInfo^` et que `textBlock` est un `TextBlock^`XAML.

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

Dans l’exemple suivant, une application cliente passe un délégué personnalisé à une méthode publique dans un composant Windows Runtime qui exécute le délégué sur chaque élément dans un `Vector`:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Construction

Vous pouvez construire un délégué à partir de l'un de ces objets :

- lambda

- fonction statique

- pointeur vers membre

- std::function

L'exemple suivant montre comment construire un délégué à partir de chacun de ces objets. Vous consommez le délégué de la même façon quel que soit le type d'objet utilisé pour la construction.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Si vous utilisez une fonction lambda qui capture le pointeur « this », veillez à utiliser l'opérateur `-=` pour annuler explicitement votre inscription à l'événement avant de quitter la fonction lambda. Pour plus d'informations, consultez [Événements](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Délégués génériques

Les délégués génériques en C++/CX ont des restrictions similaires à celles des déclarations de classes génériques. Ils ne peuvent pas être déclarés publics. Vous pouvez déclarer un délégué générique comme étant privé ou interne, et le consommer à partir du C++, mais les clients .NET ou JavaScript ne peuvent pas le consommer, car il n'est pas émis dans les métadonnées .winmd. Cet exemple déclare un délégué générique qui ne peut être consommé que par du C++ :

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

L'exemple suivant déclare une instance spécifique du délégué, à l'intérieur d'une définition de classe :

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Délégués et threads

Un délégué, comme un objet de fonction, contient le code qui s'exécute à un moment donné dans le futur. Si le code qui crée et passe le délégué, ainsi que la fonction qui accepte et exécute le délégué, s'exécutent sur le même thread, alors les choses sont relativement simples. Si ce thread est le thread d'interface utilisateur, le délégué peut directement manipuler des objets d'interface utilisateur tels que les contrôles XAML.

Si une application cliente charge un composant Windows Runtime qui s’exécute dans un thread cloisonné et fournit un délégué à ce composant, puis par défaut le délégué est appelé directement sur le thread STA. La plupart des composants Windows Runtime peut s’exécuter dans STA ou MTA.

Si le code qui exécute le délégué s'exécute sur un autre thread (par exemple, dans le contexte d'un objet concurrency::task), vous êtes alors chargé de synchroniser l'accès aux données partagées. Par exemple, si votre délégué contient une référence à un vecteur et qu'un contrôle XAML possède une référence à ce même vecteur, vous devez prendre les mesures nécessaires pour éviter les interblocages et les conditions de concurrence critiques qui peuvent se produire lorsque le délégué et le contrôle XAML tentent d'accéder au vecteur simultanément. Vous devez également veiller à ce que le délégué ne tente pas de capturer les variables locales par référence pouvant être hors de portée avant que le délégué ne soit appelé.

Si vous souhaitez que votre délégué créé soit rappelé sur le thread sur lequel il a été créé, par exemple, si vous le passez à un composant qui s'exécute dans un MTA cloisonné, et que vous souhaitez qu'il soit appelé sur le même thread que le créateur, utilisez la surcharge de constructeur délégué qui accepte un second paramètre `CallbackContext` . Utilisez uniquement cette surcharge sur les délégués avec un proxy/stub inscrits car tous les délégués qui sont définis dans Windows.winmd ne sont pas inscrits.

Si vous connaissez les gestionnaires d'événements dans .NET, vous savez qu'il est recommandé de créer une copie locale d'un événement avant de le déclencher. Cela évite les conditions de concurrence où un gestionnaire d'événements peut être supprimé juste avant l'appel de l'événement. Il n'est pas nécessaire de procéder ainsi en C++/CX, car lorsque des gestionnaires d'événements sont ajoutés ou supprimés, une liste de gestionnaires est créée. Dans la mesure où un objet C++ incrémente le nombre de références dans la liste de gestionnaires avant d'appeler un événement, vous avez la garantie que tous les gestionnaires sont valides. Toutefois, cela signifie également que si vous supprimez un gestionnaire d'événements sur le thread consommateur, ce gestionnaire peut encore être appelé si l'objet de publication continue d'utiliser sa copie de la liste, laquelle est désormais obsolète. L'objet de publication obtiendra la mise à jour de la liste la prochaine fois qu'il déclenchera l'événement.

## <a name="see-also"></a>Voir aussi

[Système de type](../cppcx/type-system-c-cx.md)<br/>
[Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence aux espaces de noms](../cppcx/namespaces-reference-c-cx.md)
