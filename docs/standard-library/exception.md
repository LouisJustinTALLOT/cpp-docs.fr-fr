---
title: '&lt;exception&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: 681baee5ac5d19e8b3ffdf37c37599c9cb68f253
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457902"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

Définit plusieurs types et fonctions relatifs à la gestion des exceptions. La gestion des exceptions est utilisée dans les situations dans lesquelles le système peut récupérer d'une erreur. Elle permet au contrôle d'être retourné au programme depuis une fonction. L'ajout de la gestion des exceptions a pour but d'augmenter la robustesse du programme et de récupérer d'une erreur de façon appropriée.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<exception>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Type qui décrit un pointeur vers une exception.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Type qui décrit un pointeur vers une fonction pouvant être utilisée comme un `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Type qui décrit un pointeur vers une fonction pouvant être utilisée comme un `unexpected_handler`.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Obtient un pointeur vers l'exception actuelle.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Obtient la fonction `terminate_handler` actuelle.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Obtient la fonction `unexpected_handler` actuelle.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Crée un objet `exception_ptr` qui contient une copie d'une exception.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Lève une exception passée comme paramètre.|
|[rethrow_if_nested](../standard-library/exception-functions.md#rethrow_if_nested)|Caste et lève une exception si imbriquée.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Génère un nouvel appel à `terminate_handler` à l'arrêt du programme.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Génère un nouveau `unexpected_handler` à appeler en cas d'exception inattendue.|
|[terminate](../standard-library/exception-functions.md#terminate)|Appelle un gestionnaire d'arrêt.|
|[throw_with_nested](../standard-library/exception-functions.md#throw_with_nested)|Lève une exception si imbriquée.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Retourne **true** uniquement si une exception levée est actuellement traitée.|
|[unexpected](../standard-library/exception-functions.md#unexpected)|Appelle un gestionnaire d'exceptions inattendues.|

### <a name="classes"></a>Classes

|||
|-|-|
|[bad_exception, classe](../standard-library/bad-exception-class.md)|La classe décrit une exception pouvant être levée depuis un `unexpected_handler`.|
|[exception, classe](../standard-library/exception-class.md)|La classe sert de classe de base pour toutes les exceptions levées par certaines expressions et par la bibliothèque C++ Standard.|
|[nested_exception, classe](../standard-library/nested-exception-class.md)|La classe décrit une exception qui peut être capturée et stockée pour une utilisation ultérieure.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
