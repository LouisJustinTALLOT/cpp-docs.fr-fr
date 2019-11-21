---
title: Pointeurs intelligents (C++ moderne)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: a18a5daa45f4f913b6b6dd714956f8592ca0a8d0
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246353"
---
# <a name="smart-pointers-modern-c"></a>Pointeurs intelligents (C++ moderne)

In modern C++ programming, the Standard Library includes *smart pointers*, which are used to help ensure that programs are free of memory and resource leaks and are exception-safe.

## <a name="uses-for-smart-pointers"></a>Utilisations pour les pointeurs intelligents

Smart pointers are defined in the `std` namespace in the [\<memory>](../standard-library/memory.md) header file. They are crucial to the [RAII](objects-own-resources-raii.md) or *Resource Acquisition Is Initialization* programming idiom. L'objectif principal de cet idiome est de garantir que l'acquisition des ressources se produit en même temps que l'initialisation de l'objet, afin que toutes les ressources de l'objet soient créées et préparées en une seule ligne de code. En pratique, le grand principe de RAII est de donner la propriété de toute ressource allouée par tas, par exemple la mémoire allouée dynamiquement ou les handles d'objet système, à un objet alloué par la pile dont le destructeur contient le code de suppression ou de libération de la ressource ainsi que le code de nettoyage associé.

Dans la plupart des cas, lorsque vous initialisez un pointeur brut ou un handle de ressource pour pointer vers une ressource réelle, passez immédiatement le pointeur à un pointeur intelligent. En C++ moderne, les pointeurs bruts sont utilisés uniquement dans les petits blocs de code à portée limitée, les boucles ou les fonctions d'assistance lorsque les performances sont essentielles et qu'il n'existe aucune chance de confusion en matière de propriété.

L'exemple suivant compare une déclaration de pointeur brut à une déclaration de pointeur intelligent.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Comme indiqué dans l'exemple, un pointeur intelligent est un modèle de classe que vous déclarez dans la pile et que vous initialisez en utilisant un pointeur brut qui pointe vers un objet alloué par tas. Une fois le pointeur intelligent initialisé, il possède le pointeur brut. Cela signifie que le pointeur intelligent est chargé de supprimer la mémoire que le pointeur brut spécifie. Le destructeur du pointeur intelligent contient l'appel à supprimer, et comme le pointeur intelligent est déclaré sur la pile, son destructeur est appelé lorsque le pointeur intelligent sort de son étendue, même si une exception est levée à un emplacement situé plus haut dans la pile.

Accédez au pointeur encapsulé en utilisant des opérateurs de pointeur familiers, `->` et `*`, que la classe de pointeur intelligent surcharge pour retourner un pointeur brut encapsulé.

L'idiome de pointeur intelligent C++ ressemble à la création d'objets dans les langages tels que C# : vous créez l'objet, puis vous laissez au système le soin de le supprimer au moment approprié. La différence vient du fait qu'aucun récupérateur de mémoire distinct ne s'exécute en arrière-plan ; la mémoire est gérée via les règles de portée C++ standard afin que l'environnement d'exécution soit plus rapide et plus efficace.

> [!IMPORTANT]
>  Veillez à toujours créer les pointeurs intelligents sur une ligne distincte de code et jamais dans une liste de paramètres, afin qu'une fuite de ressource subtile ne se produise pas suite à certaines règles d'allocation de liste de paramètres.

The following example shows how a `unique_ptr` smart pointer type from the C++ Standard Library could be used to encapsulate a pointer to a large object.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

L'exemple illustre les étapes essentielles suivantes pour utiliser les pointeurs intelligents.

1. Déclarez le pointeur intelligent comme variable automatique (locale). (Do not use the **new** or `malloc` expression on the smart pointer itself.)

1. Dans le paramètre de type, spécifiez le type pointé du pointeur encapsulé.

1. Pass a raw pointer to a **new**-ed object in the smart pointer constructor. (Certaines fonctions utilitaires ou certains constructeurs de pointeur intelligent le font à votre place.)

1. Utilisez les opérateurs `->` et `*` surchargés pour accéder à l'objet.

1. Laissez le pointeur intelligent supprimer l'objet.

Les pointeurs intelligents sont conçus pour être aussi efficaces que possible, aussi bien en termes de mémoire que de performances. Par exemple, la seule donnée membre dans `unique_ptr` est le pointeur encapsulé. Cela signifie que `unique_ptr` a exactement la même taille que ce pointeur, soit quatre octets ou huit octets. Accessing the encapsulated pointer by using the smart pointer overloaded * and -> operators is not significantly slower than accessing the raw pointers directly.

Les pointeurs intelligents ont leurs propres fonctions membres, accessibles à l'aide de la notation par « point ». For example, some C++ Standard Library smart pointers have a reset member function that releases ownership of the pointer. C'est utile lorsque vous souhaitez libérer la mémoire possédée par le pointeur intelligent avant que celui-ci ne passe hors de portée, comme illustré dans l'exemple suivant.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Les pointeurs intelligents permettent généralement d'accéder directement à leur pointeur brut. C++ Standard Library smart pointers have a `get` member function for this purpose, and `CComPtr` has a public `p` class member. En assurant l'accès direct au pointeur sous-jacent, vous pouvez utiliser le pointeur intelligent pour gérer la mémoire dans votre propre code et continuer à passer le pointeur brut au code qui ne prend pas en charge les pointeurs intelligents.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Kinds of smart pointers

La section suivante résume les différents genres de pointeurs intelligents disponibles dans l'environnement de programmation Windows, et indique quand les utiliser.

### <a name="c-standard-library-smart-pointers"></a>C++ Standard Library smart pointers

Utilisez ces pointeurs intelligents comme premier choix pour encapsuler les pointeurs vers les objets C++ anciens ordinaires (POCO).

- `unique_ptr`<br/>
   Autorise exactement un propriétaire du pointeur sous-jacent. À utiliser comme option par défaut pour POCO à moins que vous ne soyez certain d'avoir besoin de `shared_ptr`. Peut être déplacé vers un nouveau propriétaire, mais pas copié ou partagé. Remplace `auto_ptr`, qui est déconseillé. Comparez à `boost::scoped_ptr`. `unique_ptr` is small and efficient; the size is one pointer and it supports rvalue references for fast insertion and retrieval from C++ Standard Library collections. Fichier d'en-tête : `<memory>`. For more information, see [How to: Create and Use unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Pointeur intelligent de références comptabilisées. À utiliser lorsque vous souhaitez affecter un pointeur brut à plusieurs propriétaires, par exemple, lorsque vous retournez la copie d'un pointeur à partir d'un conteneur, mais que vous souhaitez conserver l'original. Le pointeur brut n'est pas supprimé tant que tous les propriétaires `shared_ptr` ne sont pas hors de portée ou n'ont pas abandonné la propriété. La taille contient deux pointeurs ; un pour l'objet et un pour le bloc de contrôle partagé qui contient le nombre de références. Fichier d'en-tête : `<memory>`. For more information, see [How to: Create and Use shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Pointeur intelligent spécifique à utiliser en collaboration avec `shared_ptr`. `weak_ptr` fournit l'accès à un objet appartenant à une ou plusieurs instances `shared_ptr`, mais ne participe pas au décompte de références. À utiliser lorsque vous souhaitez observer un objet, mais n'avez pas besoin qu'il demeure actif. Obligatoire dans certains cas pour interrompre les références circulaires entre les instances `shared_ptr`. Fichier d'en-tête : `<memory>`. For more information, see [How to: Create and Use weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Smart pointers for COM objects (classic Windows programming)

Lorsque vous travaillez avec les objets COM, encapsulez les pointeurs d'interface dans un type de pointeur intelligent approprié. La bibliothèque ATL (Active Template Library) définit plusieurs pointeurs intelligents pour différents besoins. Vous pouvez également utiliser le type pointeur intelligent `_com_ptr_t`, que le compilateur utilise lorsqu'il crée des classes wrapper à partir de fichiers .tlb. C'est le meilleur choix lorsque vous ne souhaitez pas inclure les fichiers d'en-tête ATL.

[CComPtr, classe](../atl/reference/ccomptr-class.md)<br/>
Procédez ainsi à moins que vous ne puissiez pas utiliser ATL. Effectue un décompte des références à l'aide des méthodes `AddRef` et `Release`. For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComQIPtr, classe](../atl/reference/ccomqiptr-class.md)<br/>
Ressemble à `CComPtr`, mais fournit également une syntaxe simplifiée pour appeler `QueryInterface` sur les objets COM. For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComHeapPtr, classe](../atl/reference/ccomheapptr-class.md)<br/>
Pointeur intelligent vers des objets qui utilisent `CoTaskMemFree` pour libérer de la mémoire.

[CComGITPtr, classe](../atl/reference/ccomgitptr-class.md)<br/>
Pointeur intelligent pour les interfaces obtenues à partir de la table GIT (Global Interface Table).

[_com_ptr_t, classe](com-ptr-t-class.md)<br/>
Ressemble à `CComQIPtr` en termes de fonctionnalités mais ne dépend pas d'en-têtes ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>ATL smart pointers for POCO objects

In addition to smart pointers for COM objects, ATL also defines smart pointers, and collections of smart pointers, for plain old C++ objects (POCO). In classic Windows programming, these types are useful alternatives to the C++ Standard Library collections, especially when code portability is not required or when you do not want to mix the programming models of the C++ Standard Library and ATL.

[CAutoPtr, classe](../atl/reference/cautoptr-class.md)<br/>
Pointeur intelligent qui applique une propriété unique en transférant la propriété lors de la copie. Comparable à la classe `std::auto_ptr` déconseillée.

[CHeapPtr, classe](../atl/reference/cheapptr-class.md)<br/>
Smart pointer for objects that are allocated by using the C [malloc](../c-runtime-library/reference/malloc.md) function.

[CAutoVectorPtr, classe](../atl/reference/cautovectorptr-class.md)<br/>
Pointeur intelligent pour les tableaux alloués à l'aide de `new[]`.

[CAutoPtrArray, classe](../atl/reference/cautoptrarray-class.md)<br/>
Classe qui encapsule un tableau d'éléments `CAutoPtr`.

[CAutoPtrList, classe](../atl/reference/cautoptrlist-class.md)<br/>
Classe qui encapsule les méthodes de manipulation d'une liste de nœuds `CAutoPtr`.

## <a name="see-also"></a>Voir aussi

[Pointeurs](pointers-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
