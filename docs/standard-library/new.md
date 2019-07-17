---
title: '&lt;nouveau&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: bc873f278461fcdc6dbb42e7c968c691e3dc7f73
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243547"
---
# <a name="ltnewgt"></a>&lt;nouveau&gt;

Définit plusieurs types et fonctions qui contrôlent l'allocation et la libération de stockage sous contrôle du programme. Définit également des composants pour la création de rapports sur les erreurs de gestion de stockage.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<new>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Certaines des fonctions déclarées dans cet en-tête sont remplaçables. L'implémentation fournit une version par défaut, dont le comportement est décrit dans ce document. Un programme peut toutefois définir une fonction avec la même signature pour remplacer la version par défaut au moment de la liaison. La version de remplacement doit satisfaire aux spécifications décrites dans ce document.

## <a name="members"></a>Membres

### <a name="objects"></a>Objets

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Fournit un objet à utiliser en tant qu’argument pour le **nothrow** versions de **nouveau** et **supprimer**.|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Type qui pointe vers une fonction pouvant être utilisée comme gestionnaire new.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>Fonctions

|||
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[blanchiment](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Installe une fonction utilisateur appelée quand new échoue dans sa tentative d'allocation de mémoire.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator delete](../standard-library/new-operators.md#op_delete)|Fonction appelée par une expression delete pour libérer le stockage pour des objets distincts.|
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Fonction appelée par une expression delete pour libérer le stockage pour un tableau d'objets.|
|[operator new](../standard-library/new-operators.md#op_new)|Fonction appelée par une expression new pour allouer le stockage pour des objets distincts.|
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Fonction appelée par une expression new pour allouer le stockage pour un tableau d'objets.|

### <a name="enums"></a>Enums

|||
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Classes

|||
|-|-|
|[bad_alloc, classe](../standard-library/bad-alloc-class.md)|La classe décrit une exception levée pour indiquer qu'une demande d'allocation n'a pas réussi.|
|[bad_array_new_length, classe](../standard-library/bad-array-new-length.md)||
|[nothrow_t, classe](../standard-library/nothrow-t-structure.md)|La classe est utilisée comme paramètre de fonction de l'opérateur new pour indiquer que la fonction doit retourner un pointeur null pour signaler un échec d'allocation, au lieu de lever une exception.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
