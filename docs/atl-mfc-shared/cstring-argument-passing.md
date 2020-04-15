---
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
ms.openlocfilehash: 53977eb47520a20571a2d5ba8aa105c567ff40d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317933"
---
# <a name="cstring-argument-passing"></a>Passage d’arguments CString

Cet article explique comment transmettre les objets [CString](../atl-mfc-shared/reference/cstringt-class.md) `CString` aux fonctions et comment retourner les objets des fonctions.

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a>CString Argument-Passing Conventions

Lorsque vous définissez une interface de classe, vous devez déterminer la convention argument-passage pour vos fonctions de membre. Il existe des règles standard `CString` pour le passage et le retour des objets. Si vous suivez les règles [décrites](#_core_strings_as_function_inputs) dans les chaînes comme les entrées de fonction et [les chaînes comme sorties de fonction,](#_core_strings_as_function_outputs)vous aurez un code efficace et correct.

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a>Cordes comme entrées de fonction

La façon la plus efficace `CString` et la plus sûre d’utiliser un objet dans les fonctions appelées est de passer un `CString` objet à la fonction. Malgré le nom, un `CString` objet ne stocke pas une chaîne interne comme une chaîne de style C qui a un terminateur nul. Au lieu `CString` de cela, un objet garde une trace attentive du nombre de caractères qu’il a. Avoir `CString` fourni un pointeur LPCTSTR à une chaîne annulée est une petite quantité de travail qui peut devenir important si votre code doit le faire constamment. Le résultat est temporaire parce `CString` que toute modification du contenu invalide les anciennes copies du pointeur LPCTSTR.

Il est logique dans certains cas de fournir une chaîne de style C. Par exemple, il peut y avoir une situation où une fonction appelée est écrite en C et ne prend pas en charge les objets. Dans ce cas, `CString` contraindre le paramètre à LPCTSTR, et la fonction obtiendra une corde de type C non terminée. Vous pouvez également aller dans `CString` l’autre `CString` sens et créer un objet en utilisant le constructeur qui accepte un paramètre de chaîne de style C.

Si le contenu de la chaîne doit être modifié par une `CString` fonction, déclarez le paramètre comme une référence nonconstante ().`CString&`

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a>Cordes comme sorties de fonction

Typiquement, vous `CString` pouvez retourner `CString` des objets à partir de fonctions parce que les objets suivent la sémantique de valeur comme les types primitifs. Pour retourner une chaîne de lecture `CString` seulement, utilisez une référence constante (`const CString&`). L’exemple suivant illustre `CString` l’utilisation de paramètres et de types de retour :

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Cordes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
