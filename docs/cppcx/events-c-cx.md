---
title: Événements (C + c++ / CX) | Documents Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98231f0803270a9e033529e163ff2cc23cdd64e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089636"
---
# <a name="events-ccx"></a>Événements (C++/CX)
Un objet Windows Runtime type peut déclarer (qui est, publier) les événements et le code client dans le même composant ou dans d’autres composants peuvent s’abonner à ces événements en associant des méthodes appelées *gestionnaires d’événements* avec l’événement. Plusieurs gestionnaires d'événements peuvent être associés à un seul événement. Lorsque l'objet de publication déclenche l'événement, il entraîne l'appel de tous les gestionnaires d'événements. Ainsi, une classe d'abonnement peut effectuer l'action personnalisée appropriée lorsque l'éditeur déclenche l'événement. Un événement a un type délégué qui spécifie la signature que tous les gestionnaires d'événements doivent posséder pour s'abonner à l'événement.  
  
## <a name="consuming-events-in-windows-components"></a>Utilisation d'événements dans les composants Windows  
 De nombreux composants dans le Windows Runtime exposent des événements. Par exemple, un objet LightSensor déclenche un événement ReadingChanged lorsque le capteur signale une nouvelle valeur de luminescence. Lorsque vous utilisez un objet LightSensor dans votre programme, vous pouvez définir une méthode qui est appelée lorsque l'événement ReadingChanged se déclenche. La méthode peut faire tout ce que vous voulez faire ; la seule exigence est que sa signature doit correspondre à la signature du délégué pour plus d’informations sur la façon de créer un gestionnaire d’événements délégué et l’abonnement à un événement, consultez [délégués](../cppcx/delegates-c-cx.md).  
  
## <a name="creating-custom-events"></a>Création d'événements personnalisés  
  
### <a name="declaration"></a>Déclaration  
 Vous pouvez déclarer un événement dans une interface ou une classe ref, et celui-ci peut avoir un accès public, interne (public/privé), protégé public, protégé, protégé privé ou privé. Lorsque vous déclarez un événement, le compilateur crée de façon interne un objet qui expose deux méthodes d'accesseur : add et remove. Lorsque des objets d'abonnement inscrivent des gestionnaires d'événements, l'objet événement les stocke dans une collection. Lorsqu'un événement est déclenché, l'objet événement appelle tous les gestionnaires de sa liste, chacun à leur tour. Un événement trivial (comme celui illustré dans l'exemple suivant) détient un magasin de stockage implicite, ainsi que des méthodes d'accesseur `add` et `remove` implicites. Vous pouvez également spécifier vos propres accesseurs, de la même façon que vous pouvez spécifier des accesseurs `get` et `set` personnalisés pour une propriété.  La classe d'implémentation ne peut pas parcourir manuellement la liste d'abonnés dans un événement trivial.  
  
 L'exemple suivant montre comment déclarer et déclencher un événement : Notez que l'événement a un type délégué et est déclaré à l'aide du symbole « ^ ».  
  
 [!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]  
  
### <a name="usage"></a>Utilisation  
 L'exemple suivant montre comment une classe d'abonnement utilise l'opérateur `+=` pour s'abonner à l'événement et fournir un gestionnaire d'événements à appeler lorsque l'événement se déclenche. Notez que la fonction qui est fournie correspond à la signature du délégué défini côté serveur de publication dans l'espace de noms `EventTest` .  
  
 [!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]  
  
> [!WARNING]
>  En général, il est préférable d'utiliser une fonction nommée, plutôt qu'une fonction lambda, pour un gestionnaire d'événements à moins que vous ne souhaitiez particulièrement éviter les références circulaires. Une fonction nommée capture le pointeur « this » par une référence faible, tandis qu'une fonction lambda le capture par une référence forte et crée une référence circulaire. Pour plus d'informations, consultez [Références faibles et cycles avec rupture (C++/CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).  
  
### <a name="custom-add-and-remove-methods"></a>Méthodes add et remove personnalisées  
 En interne, un événement contient une méthode add, une méthode remove et une méthode raise. Lorsque le code client s'abonne à un événement, la méthode add est appelée et le délégué qui est passé est ajouté à la liste des appels de l'événement. La classe d'édition appelle l'événement, elle provoque la méthode raise() à appeler, et chaque délégué de la liste est appelé à son tour. Un abonné peut se supprimer de la liste de délégués, ce qui provoque l'appel de la méthode de suppression de l'événement. Le compilateur fournit les versions par défaut de ces méthodes si vous ne les définissez pas dans votre code ; ils sont appelés événements triviaux. Dans de nombreux cas, un événement trivial constitue l'unique exigence.  
  
 Vous pouvez spécifier des méthodes add, remove et raise personnalisées pour un événement si vous devez exécuter une logique personnalisée en réponse à l'ajout ou la suppression d'abonnés. Par exemple, si vous avez un objet coûteux qui est uniquement requis pour l'enregistrement d'événements, vous pouvez différer la création de l'objet jusqu'à ce qu'un client s'abonne réellement à l'événement.  
  
 L'exemple suivant indique comment ajouter des méthodes add, remove et raise personnalisées à un événement :  
  
 [!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]  
  
## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Suppression d'un gestionnaire d'événements du côté abonné  
 Dans certains cas rares, vous pouvez supprimer un gestionnaire d'événements pour un événement auquel vous vous êtes précédemment abonné. Par exemple, vous pouvez le remplacer par un autre gestionnaire d'événements ou vous pouvez supprimer des ressources qui sont détenues par celui-ci. Pour supprimer un gestionnaire, vous devez enregistrer EventRegistrationToken qui est retourné par l'opération `+=` . Vous pouvez ensuite utiliser l'opérateur `-=` du jeton pour supprimer un gestionnaire d'événements.  Toutefois, le gestionnaire d'origine peut être appelé même après avoir été supprimé. Par conséquent, si vous avez l'intention de supprimer un gestionnaire d'événements, créez un indicateur membre et définissez-le si l'événement est supprimé, puis dans le gestionnaire d'événements, vérifiez l'indicateur et retournez immédiatement la valeur s'il est défini. L'exemple suivant illustre le modèle de base.  
  
 [!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]  
  
### <a name="remarks"></a>Notes  
 Plusieurs gestionnaires peuvent être associés au même événement. La source d'événements appelle de manière séquentielle tous les gestionnaires d'événements du même thread. Si un récepteur d'événements bloque dans la méthode de gestionnaire d'événements, il empêche la source d'événements d'appeler d'autres gestionnaires d'événements pour cet événement.  
  
 L'ordre dans lequel la source d'événements appelle les gestionnaires d'événements sur les récepteurs d'événements n'est pas garanti et peut différer d'un appel à un autre.  
  
## <a name="see-also"></a>Voir aussi  
 [Système de type](../cppcx/type-system-c-cx.md)   
 [Délégués](../cppcx/delegates-c-cx.md)   
 [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)