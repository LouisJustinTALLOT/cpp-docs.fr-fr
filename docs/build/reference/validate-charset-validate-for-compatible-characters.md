---
title: -valider-charset (valider les caractères compatibles) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- /validate-charset
- validate-charset
dev_langs:
- C++
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0804d9d2714cc8c4f065b6908788c067c34ca44b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377386"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/ Validate-CharSet (valider les caractères compatibles)
Vérifie que le texte du fichier source contient uniquement des caractères pouvant être représentées au format UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/validate-charset[-]  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la **/Validate-CharSet** option permettant de valider que le code source contient uniquement des caractères qui peuvent être représentées dans les deux caractères de code source et de jeu de caractères d’exécution. Cette vérification est activée automatiquement lorsque vous spécifiez **/source-CharSet**, **/Execution-CharSet**, ou **/UTF-8** options du compilateur. Vous pouvez désactiver explicitement cette vérification en spécifiant le **/ validate-charset -** option.  
  
 Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est encodé au format Unicode, par exemple, UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvé, il suppose que le fichier source est encodé à l’aide de la page de code utilisateur actuel, sauf si vous avez spécifié une page de codes à l’aide de **/UTF-8** ou **/source-CharSet** option. Visual Studio vous permet d’enregistrer votre code source C++ à l’aide de plusieurs codages de caractères. Pour plus d’informations sur les jeux de caractères source et de l’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation de langage. Pour une liste de prise en charge les identificateurs de page de code et les noms de jeu de caractères, consultez [Code Page Identifiers](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Visual Studio utilise UTF-8 comme encodage de caractères interne lors de la conversion entre le jeu de caractères source et le jeu de caractères d’exécution. Si un caractère dans le fichier source ne peut pas être représenté dans le jeu de caractères d’exécution, la conversion de UTF-8 substitue un point d’interrogation ' ?' caractères. Le **/Validate-CharSet** option entraîne la compilation signaler un avertissement si cela se produit.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration**, **C/C++**, **ligne de commande** dossier.  
  
3.  Dans **Options avancées**, ajoutez le **/Validate-CharSet** option, puis spécifiez votre encodage préféré.  
  
4.  Choisissez **OK** pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/ source-CharSet (définir Source Character Set)](../../build/reference/source-charset-set-source-character-set.md)   
 [/utf-8 (Définir les jeux de caractères sources et exécutables sur UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)