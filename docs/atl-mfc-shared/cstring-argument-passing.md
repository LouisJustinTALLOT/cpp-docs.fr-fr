---
title: Passage d’arguments CString | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 642ff20028a0929bb7bc11815e66b9f845ef9bd7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356828"
---
# <a name="cstring-argument-passing"></a>Passage d’arguments CString
Cet article explique comment passer [CString](../atl-mfc-shared/reference/cstringt-class.md) aux fonctions et comment retourner des objets de `CString` objets à partir de fonctions.  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> Conventions de transmission des arguments CString  
 Lorsque vous définissez une interface de classe, vous devez déterminer la convention de passage des arguments pour les fonctions membres. Il existe quelques règles standard pour passer et retourner `CString` objets. Si vous suivez les règles décrites dans [chaînes en tant qu’entrée de fonction](#_core_strings_as_function_inputs) et [chaînes en tant que sortie de fonction](#_core_strings_as_function_outputs), vous aurez un code efficace et correct.  
  
##  <a name="_core_strings_as_function_inputs"></a> Chaînes en tant qu’entrée de fonction  
 La façon la plus efficace et sécurisée à utiliser un `CString` objet dans les fonctions appelées consiste à passer un `CString` objet à la fonction. Malgré son nom, un `CString` objet ne pas stocke une chaîne en interne comme une chaîne de style C qui possède un terminateur null. Au lieu de cela, un `CString` objet suivi attention au nombre de caractères qu’il a. Avoir `CString` fournissent un `LPCTSTR` pointeur vers une chaîne se terminant par null est une petite quantité de travail peut devenir important si votre code doit faire en permanence. Le résultat est temporaire, car toute modification apportée à la `CString` contenu invalide les anciennes copies de la `LPCTSTR` pointeur.  
  
 Il n’est pertinent dans certains cas, fournir une chaîne de style C. Par exemple, il peut être une situation dans laquelle une fonction appelée est écrite en C ne prend pas en charge les objets. Dans ce cas, forcer le `CString` paramètre `LPCTSTR`, et la fonction obtient une chaîne de style C se terminant par null. Vous pouvez également l’autre direction et créer un `CString` objet à l’aide de la `CString` constructeur qui accepte un paramètre de chaîne de style C.  
  
 Si le contenu de chaîne doivent être modifiés par une fonction, déclarez le paramètre en tant que non constantes `CString` référence (**CString &**).  
  
##  <a name="_core_strings_as_function_outputs"></a> Chaînes en tant que sortie de fonction  
 En général, vous pouvez retourner `CString` , car des objets à partir de fonctions `CString` objets suivent la sémantique de valeur comme des types primitifs. Pour retourner une chaîne en lecture seule, utilisez une constante `CString` référence (**const CString &**). L’exemple suivant illustre l’utilisation de `CString` paramètres et types de retour :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

