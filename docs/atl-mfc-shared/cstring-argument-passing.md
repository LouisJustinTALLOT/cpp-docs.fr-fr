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
ms.openlocfilehash: bf18265e19e4b1c1db010a4d7638fa959c357bca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562394"
---
# <a name="cstring-argument-passing"></a>Passage d’arguments CString

Cet article explique comment passer [CString](../atl-mfc-shared/reference/cstringt-class.md) objets à des fonctions et comment retourner `CString` objets à partir de fonctions.

##  <a name="_core_cstring_argument.2d.passing_conventions"></a> Conventions de transmission d’arguments CString

Lorsque vous définissez une interface de classe, vous devez déterminer la convention de passage d’argument pour les fonctions membres. Il existe des règles standards pour passer et retourner `CString` objets. Si vous suivez les règles décrites dans [chaînes en tant qu’entrées de fonction](#_core_strings_as_function_inputs) et [chaînes en tant que sortie de fonction](#_core_strings_as_function_outputs), vous aurez un code efficace et correct.

##  <a name="_core_strings_as_function_inputs"></a> Chaînes en tant qu’entrées de fonction

La façon la plus efficace et sécurisée à utiliser un `CString` objet dans les fonctions appelées consiste à passer un `CString` objet à la fonction. Malgré son nom, un `CString` objet ne pas stocke une chaîne en interne comme une chaîne de style C qui possède un terminateur null. Au lieu de cela, un `CString` objet suivi attention au nombre de caractères qu’il a. Avoir `CString` fournir un pointeur LPCTSTR vers une chaîne se terminant par null est une petite quantité de travail peut devenir importante si votre code doit faire en permanence. Le résultat est temporaire, car toute modification apportée à la `CString` contenu invalide les anciennes copies du pointeur LPCTSTR.

Il n’est pertinent dans certains cas, de fournir une chaîne de style C. Par exemple, il peut être une situation où une fonction appelée est écrite en C et ne prend pas en charge les objets. Dans ce cas, forcer le `CString` paramètre aux fonctions LPCTSTR et obtenez une chaîne se terminant par null de style C. Vous pouvez également l’autre sens et créer un `CString` objet à l’aide de la `CString` constructeur qui accepte un paramètre de chaîne de style C.

Si le contenu de chaîne doivent être modifiées par une fonction, déclarez le paramètre en tant que non constantes `CString` référence (`CString&`).

##  <a name="_core_strings_as_function_outputs"></a> Chaînes en tant que sortie de fonction

En général, vous pouvez retourner `CString` , car des objets à partir de fonctions `CString` objets suivent la sémantique de valeur comme des types primitifs. Pour retourner une chaîne en lecture seule, utilisez une constante `CString` référence (`const CString&`). L’exemple suivant illustre l’utilisation de `CString` paramètres et types de retour :

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

