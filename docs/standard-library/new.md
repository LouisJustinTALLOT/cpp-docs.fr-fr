---
description: 'En savoir plus sur : &lt; nouveau&gt;'
title: '&lt;nouveau&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: c99c036a7b4065e207bfe9ad71eb86e6d5f01d0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338149"
---
# <a name="ltnewgt"></a>&lt;nouveau&gt;

Définit plusieurs types et fonctions qui contrôlent l'allocation et la libération de stockage sous contrôle du programme. Définit également des composants pour la création de rapports sur les erreurs de gestion de stockage.

## <a name="requirements"></a>Spécifications

**En-tête :**\<new>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Certaines des fonctions déclarées dans cet en-tête sont remplaçables. L'implémentation fournit une version par défaut, dont le comportement est décrit dans ce document. Un programme peut toutefois définir une fonction avec la même signature pour remplacer la version par défaut au moment de la liaison. La version de remplacement doit satisfaire aux spécifications décrites dans ce document.

## <a name="members"></a>Membres

### <a name="objects"></a>Objets

|Nom|Description|
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Fournit un objet à utiliser comme argument pour les **`nothrow`** versions de **`new`** et **`delete`** .|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Type qui pointe vers une fonction pouvant être utilisée comme gestionnaire new.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[blanchi](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Installe une fonction utilisateur appelée quand new échoue dans sa tentative d'allocation de mémoire.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur delete](../standard-library/new-operators.md#op_delete)|Fonction appelée par une expression delete pour libérer le stockage pour des objets distincts.|
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Fonction appelée par une expression delete pour libérer le stockage pour un tableau d'objets.|
|[New, opérateur](../standard-library/new-operators.md#op_new)|Fonction appelée par une expression new pour allouer le stockage pour des objets distincts.|
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Fonction appelée par une expression new pour allouer le stockage pour un tableau d'objets.|

### <a name="enums"></a>Énumérations

|Nom|Description|
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[Classe bad_alloc](../standard-library/bad-alloc-class.md)|La classe décrit une exception levée pour indiquer qu'une demande d'allocation n'a pas réussi.|
|[Classe bad_array_new_length](../standard-library/bad-array-new-length.md)||
|[nothrow_t, classe](../standard-library/nothrow-t-structure.md)|La classe est utilisée comme paramètre de fonction de l'opérateur new pour indiquer que la fonction doit retourner un pointeur null pour signaler un échec d'allocation, au lieu de lever une exception.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
