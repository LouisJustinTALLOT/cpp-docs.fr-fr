---
title: '&lt;new&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <new>
dev_langs:
- C++
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17a72100dbfb51fae9085e3900cd180bde0a31be
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ltnewgt"></a>&lt;new&gt;

Définit plusieurs types et fonctions qui contrôlent l'allocation et la libération de stockage sous contrôle du programme. Définit également des composants pour la création de rapports sur les erreurs de gestion de stockage.

## <a name="syntax"></a>Syntaxe

```cpp
#include <new>

```

## <a name="remarks"></a>Notes

Certaines des fonctions déclarées dans cet en-tête sont remplaçables. L'implémentation fournit une version par défaut, dont le comportement est décrit dans ce document. Un programme peut toutefois définir une fonction avec la même signature pour remplacer la version par défaut au moment de la liaison. La version de remplacement doit satisfaire aux spécifications décrites dans ce document.

### <a name="objects"></a>Objets

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Fournit un objet à utiliser comme argument pour les versions `nothrow` de **new** et **delete**.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Type qui pointe vers une fonction pouvant être utilisée comme gestionnaire new.|

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Installe une fonction utilisateur appelée quand new échoue dans sa tentative d'allocation de mémoire.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator delete](../standard-library/new-operators.md#op_delete)|Fonction appelée par une expression delete pour libérer le stockage pour des objets distincts.|
|[operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Fonction appelée par une expression delete pour libérer le stockage pour un tableau d'objets.|
|[operator new](../standard-library/new-operators.md#op_new)|Fonction appelée par une expression new pour allouer le stockage pour des objets distincts.|
|[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Fonction appelée par une expression new pour allouer le stockage pour un tableau d'objets.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[bad_alloc, classe](../standard-library/bad-alloc-class.md)|La classe décrit une exception levée pour indiquer qu'une demande d'allocation n'a pas réussi.|
|[nothrow_t, classe](../standard-library/nothrow-t-structure.md)|La classe est utilisée comme paramètre de fonction de l'opérateur new pour indiquer que la fonction doit retourner un pointeur null pour signaler un échec d'allocation, au lieu de lever une exception.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
