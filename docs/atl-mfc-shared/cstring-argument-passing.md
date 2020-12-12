---
description: 'En savoir plus sur : passage de l’argument CString'
title: Passage d’arguments CString
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: ee47898ffdfc5129b11b0f9480669fa142d12818
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167173"
---
# <a name="cstring-argument-passing"></a>Passage d’arguments CString

Cet article explique comment passer des objets [CString](../atl-mfc-shared/reference/cstringt-class.md) à des fonctions et comment retourner `CString` des objets à partir de fonctions.

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a> Conventions de Argument-Passing CString

Lorsque vous définissez une interface de classe, vous devez déterminer la Convention de passage d’argument pour vos fonctions membres. Il existe des règles standard pour le transfert et le retour d' `CString` objets. Si vous suivez les règles décrites dans [chaînes en tant que entrées de fonction](#_core_strings_as_function_inputs) et [chaînes en tant que sorties de fonction](#_core_strings_as_function_outputs), vous obtiendrez un code efficace et correct.

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a> Chaînes en tant qu’entrées de fonction

La méthode la plus efficace et sécurisée pour utiliser un `CString` objet dans les fonctions appelées consiste à passer un `CString` objet à la fonction. Malgré le nom, un `CString` objet ne stocke pas de chaîne en interne comme une chaîne de style C qui a un terminateur null. Au lieu de `CString` cela, un objet garde une trace soignée du nombre de caractères qu’il a. `CString`Le fait de fournir un pointeur LPCTSTR vers une chaîne se terminant par un caractère NULL est une petite quantité de travail qui peut devenir significative si votre code doit le faire en permanence. Le résultat est temporaire, car toute modification apportée au `CString` contenu invalide les anciennes copies du pointeur LPCTSTR.

Dans certains cas, il est logique de fournir une chaîne de style C. Par exemple, il peut y avoir une situation où une fonction appelée est écrite en C et ne prend pas en charge les objets. Dans ce cas, forcez le `CString` paramètre à la valeur LPCTSTR et la fonction obtiendra une chaîne se terminant par un caractère null de style C. Vous pouvez également accéder à l’autre direction et créer un `CString` objet à l’aide du `CString` constructeur qui accepte un paramètre de chaîne de style C.

Si le contenu de la chaîne doit être modifié par une fonction, déclarez le paramètre en tant que référence non constante `CString` ( `CString&` ).

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a> Chaînes en tant que sorties de fonction

En général, vous pouvez retourner `CString` des objets à partir de fonctions, car les `CString` objets suivent la sémantique des valeurs comme les types primitifs. Pour retourner une chaîne en lecture seule, utilisez une référence de constante `CString` ( `const CString&` ). L’exemple suivant illustre l’utilisation des `CString` paramètres et des types de retour :

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
