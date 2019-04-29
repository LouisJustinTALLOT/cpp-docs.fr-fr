---
title: Pointeurs intelligents (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: c976f9ec72929f2c8ff91fb9f9594d91c7457365
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331023"
---
# <a name="smart-pointers-modern-c"></a>Pointeurs intelligents (Modern C++)

Dans la programmation C++ moderne, la bibliothèque Standard inclut *intelligente des pointeurs*, qui sont utilisées pour garantir que les programmes sont libres de mémoire et les fuites de ressources et sont protégé contre les exceptions.

## <a name="uses-for-smart-pointers"></a>Utilisations pour les pointeurs intelligents

Pointeurs intelligents sont définis dans le `std` espace de noms dans le [ \<mémoire >](../standard-library/memory.md) fichier d’en-tête. Ils sont essentiels à la [RAII](../cpp/objects-own-resources-raii.md) ou *Resource Acquisition Is Initialization* idiome de programmation. L'objectif principal de cet idiome est de garantir que l'acquisition des ressources se produit en même temps que l'initialisation de l'objet, afin que toutes les ressources de l'objet soient créées et préparées en une seule ligne de code. En pratique, le grand principe de RAII est de donner la propriété de toute ressource allouée par tas, par exemple la mémoire allouée dynamiquement ou les handles d'objet système, à un objet alloué par la pile dont le destructeur contient le code de suppression ou de libération de la ressource ainsi que le code de nettoyage associé.

Dans la plupart des cas, lorsque vous initialisez un pointeur brut ou un handle de ressource pour pointer vers une ressource réelle, passez immédiatement le pointeur à un pointeur intelligent. En C++ moderne, les pointeurs bruts sont utilisés uniquement dans les petits blocs de code à portée limitée, les boucles ou les fonctions d'assistance lorsque les performances sont essentielles et qu'il n'existe aucune chance de confusion en matière de propriété.

L'exemple suivant compare une déclaration de pointeur brut à une déclaration de pointeur intelligent.

[!code-cpp[smart_pointers_intro#1](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Comme indiqué dans l'exemple, un pointeur intelligent est un modèle de classe que vous déclarez dans la pile et que vous initialisez en utilisant un pointeur brut qui pointe vers un objet alloué par tas. Une fois le pointeur intelligent initialisé, il possède le pointeur brut. Cela signifie que le pointeur intelligent est chargé de supprimer la mémoire que le pointeur brut spécifie. Le destructeur du pointeur intelligent contient l'appel à supprimer, et comme le pointeur intelligent est déclaré sur la pile, son destructeur est appelé lorsque le pointeur intelligent sort de son étendue, même si une exception est levée à un emplacement situé plus haut dans la pile.

Accédez au pointeur encapsulé en utilisant des opérateurs de pointeur familiers, `->` et `*`, que la classe de pointeur intelligent surcharge pour retourner un pointeur brut encapsulé.

L'idiome de pointeur intelligent C++ ressemble à la création d'objets dans les langages tels que C# : vous créez l'objet, puis vous laissez au système le soin de le supprimer au moment approprié. La différence vient du fait qu'aucun récupérateur de mémoire distinct ne s'exécute en arrière-plan ; la mémoire est gérée via les règles de portée C++ standard afin que l'environnement d'exécution soit plus rapide et plus efficace.

> [!IMPORTANT]
>  Veillez à toujours créer les pointeurs intelligents sur une ligne distincte de code et jamais dans une liste de paramètres, afin qu'une fuite de ressource subtile ne se produise pas suite à certaines règles d'allocation de liste de paramètres.

L’exemple suivant montre comment un `unique_ptr` type pointeur intelligent à partir de la bibliothèque C++ Standard peut être utilisé pour encapsuler un pointeur vers un objet volumineux.

[!code-cpp[smart_pointers_intro#2](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

L'exemple illustre les étapes essentielles suivantes pour utiliser les pointeurs intelligents.

1. Déclarez le pointeur intelligent comme variable automatique (locale). (N’utilisez pas le **nouveau** ou `malloc` expression sur le pointeur intelligent lui-même.)

1. Dans le paramètre de type, spécifiez le type pointé du pointeur encapsulé.

1. Passez un pointeur brut à un **nouveau**-objet dans le constructeur de pointeur intelligent. (Certaines fonctions utilitaires ou certains constructeurs de pointeur intelligent le font à votre place.)

1. Utilisez les opérateurs `->` et `*` surchargés pour accéder à l'objet.

1. Laissez le pointeur intelligent supprimer l'objet.

Les pointeurs intelligents sont conçus pour être aussi efficaces que possible, aussi bien en termes de mémoire que de performances. Par exemple, la seule donnée membre dans `unique_ptr` est le pointeur encapsulé. Cela signifie que `unique_ptr` a exactement la même taille que ce pointeur, soit quatre octets ou huit octets. L’accès à du pointeur encapsulé en utilisant le pointeur intelligent surchargé * et -> opérateurs n’est pas beaucoup plus lent que l’accès à des pointeurs bruts directement.

Les pointeurs intelligents ont leurs propres fonctions membres, accessibles à l'aide de la notation par « point ». Par exemple, certains pointeurs intelligents de bibliothèque Standard C++ ont une fonction de membre de réinitialisation qui libère la propriété du pointeur. C'est utile lorsque vous souhaitez libérer la mémoire possédée par le pointeur intelligent avant que celui-ci ne passe hors de portée, comme illustré dans l'exemple suivant.

[!code-cpp[smart_pointers_intro#3](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Les pointeurs intelligents permettent généralement d'accéder directement à leur pointeur brut. Pointeurs intelligents de bibliothèque C++ Standard ont un `get` fonction membre à cet effet, et `CComPtr` a un public `p` membre de classe. En assurant l'accès direct au pointeur sous-jacent, vous pouvez utiliser le pointeur intelligent pour gérer la mémoire dans votre propre code et continuer à passer le pointeur brut au code qui ne prend pas en charge les pointeurs intelligents.

[!code-cpp[smart_pointers_intro#4](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Genres de pointeurs intelligents

La section suivante résume les différents genres de pointeurs intelligents disponibles dans l'environnement de programmation Windows, et indique quand les utiliser.

### <a name="c-standard-library-smart-pointers"></a>Pointeurs intelligents de bibliothèque standard C++

Utilisez ces pointeurs intelligents comme premier choix pour encapsuler les pointeurs vers les objets C++ anciens ordinaires (POCO).

- `unique_ptr`<br/>
   Autorise exactement un propriétaire du pointeur sous-jacent. À utiliser comme option par défaut pour POCO à moins que vous ne soyez certain d'avoir besoin de `shared_ptr`. Peut être déplacé vers un nouveau propriétaire, mais pas copié ou partagé. Remplace `auto_ptr`, qui est déconseillé. Comparez à `boost::scoped_ptr`. `unique_ptr` est petite et efficace ; la taille est un pointeur, et il prend en charge les références rvalue pour une insertion rapide et l’extraction des collections de la bibliothèque C++ Standard. Fichier d'en-tête : `<memory>`. Pour plus d'informations, voir [Procédure : Créer et utiliser des Instances unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md) et [unique_ptr, classe](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Pointeur intelligent de références comptabilisées. À utiliser lorsque vous souhaitez affecter un pointeur brut à plusieurs propriétaires, par exemple, lorsque vous retournez la copie d'un pointeur à partir d'un conteneur, mais que vous souhaitez conserver l'original. Le pointeur brut n'est pas supprimé tant que tous les propriétaires `shared_ptr` ne sont pas hors de portée ou n'ont pas abandonné la propriété. La taille contient deux pointeurs ; un pour l'objet et un pour le bloc de contrôle partagé qui contient le nombre de références. Fichier d'en-tête : `<memory>`. Pour plus d'informations, voir [Procédure : Créer et utiliser des Instances shared_ptr](../cpp/how-to-create-and-use-shared-ptr-instances.md) et [shared_ptr, classe](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Pointeur intelligent spécifique à utiliser en collaboration avec `shared_ptr`. `weak_ptr` fournit l'accès à un objet appartenant à une ou plusieurs instances `shared_ptr`, mais ne participe pas au décompte de références. À utiliser lorsque vous souhaitez observer un objet, mais n'avez pas besoin qu'il demeure actif. Obligatoire dans certains cas pour interrompre les références circulaires entre les instances `shared_ptr`. Fichier d'en-tête : `<memory>`. Pour plus d'informations, voir [Procédure : Créer et utiliser des Instances weak_ptr](../cpp/how-to-create-and-use-weak-ptr-instances.md) et [weak_ptr, classe](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Pointeurs intelligents pour les objets COM (programmation Windows classique)

Lorsque vous travaillez avec les objets COM, encapsulez les pointeurs d'interface dans un type de pointeur intelligent approprié. La bibliothèque ATL (Active Template Library) définit plusieurs pointeurs intelligents pour différents besoins. Vous pouvez également utiliser le type pointeur intelligent `_com_ptr_t`, que le compilateur utilise lorsqu'il crée des classes wrapper à partir de fichiers .tlb. C'est le meilleur choix lorsque vous ne souhaitez pas inclure les fichiers d'en-tête ATL.

[CComPtr, classe](../atl/reference/ccomptr-class.md)<br/>
Procédez ainsi à moins que vous ne puissiez pas utiliser ATL. Effectue un décompte des références à l'aide des méthodes `AddRef` et `Release`. Pour plus d'informations, voir [Procédure : Créer et utiliser des Instances CComPtr et CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComQIPtr, classe](../atl/reference/ccomqiptr-class.md)<br/>
Ressemble à `CComPtr`, mais fournit également une syntaxe simplifiée pour appeler `QueryInterface` sur les objets COM. Pour plus d'informations, voir [Procédure : Créer et utiliser des Instances CComPtr et CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComHeapPtr, classe](../atl/reference/ccomheapptr-class.md)<br/>
Pointeur intelligent vers des objets qui utilisent `CoTaskMemFree` pour libérer de la mémoire.

[CComGITPtr, classe](../atl/reference/ccomgitptr-class.md)<br/>
Pointeur intelligent pour les interfaces obtenues à partir de la table GIT (Global Interface Table).

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)<br/>
Ressemble à `CComQIPtr` en termes de fonctionnalités mais ne dépend pas d'en-têtes ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>Pointeurs intelligents ATL pour objets POCO

En plus des pointeurs intelligents pour objets COM, ATL définit également des pointeurs intelligents et des collections de pointeurs intelligents pour les objets POD (Plain Old Data) de C++. Dans la programmation Windows classique, ces types sont des alternatives utiles pour les collections de la bibliothèque C++ Standard, en particulier lorsque la portabilité du code n’est pas nécessaire ou lorsque vous ne souhaitez pas mélanger les modèles de programmation de la bibliothèque Standard C++ et ATL.

[CAutoPtr, classe](../atl/reference/cautoptr-class.md)<br/>
Pointeur intelligent qui applique une propriété unique en transférant la propriété lors de la copie. Comparable à la classe `std::auto_ptr` déconseillée.

[CHeapPtr, classe](../atl/reference/cheapptr-class.md)<br/>
Pointeur intelligent pour les objets qui sont alloués à l’aide de la C [malloc](../c-runtime-library/reference/malloc.md) (fonction).

[CAutoVectorPtr, classe](../atl/reference/cautovectorptr-class.md)<br/>
Pointeur intelligent pour les tableaux alloués à l'aide de `new[]`.

[CAutoPtrArray, classe](../atl/reference/cautoptrarray-class.md)<br/>
Classe qui encapsule un tableau d'éléments `CAutoPtr`.

[CAutoPtrList, classe](../atl/reference/cautoptrlist-class.md)<br/>
Classe qui encapsule les méthodes de manipulation d'une liste de nœuds `CAutoPtr`.

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++ (C++ moderne)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
