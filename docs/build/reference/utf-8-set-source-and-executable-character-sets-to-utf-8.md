---
title: -utf-8 (définir la Source et exécutable jeux au format UTF-8 de caractères) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- /utf-8
dev_langs:
- C++
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9002d1989d9f46de29efb7b7c9a940315a99d2b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214800"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/ UTF-8 (définir la Source et le fichier exécutable jeux de caractères UTF-8)
Spécifie le jeu de caractères source et de jeu de caractères d’exécution au format UTF-8.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/utf-8  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la **/UTF-8** option pour spécifier les jeux de caractères de la source et l’exécution en tant que codé en UTF-8. Il est équivalent à la spécification **/source-charset:utf-/execution 8-charset:utf-8** sur la ligne de commande. Aucune de ces options également permet la **/Validate-CharSet** option par défaut. Pour une liste de prise en charge les identificateurs de page de code et les noms de jeu de caractères, consultez [Code Page Identifiers](/windows/desktop/Intl/code-page-identifiers).  
  
 Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est encodé au format Unicode, par exemple, UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvé, il part du principe que le fichier source est encodé à l’aide de la page de codes utilisateur actuel, sauf si vous avez spécifié une page de codes à l’aide de **/UTF-8** ou **/source-CharSet** option. Visual Studio vous permet d’enregistrer votre code source C++ à l’aide des plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration**, **C/C++**, **ligne de commande** dossier.  
  
3.  Dans **Options avancées**, ajoutez le **/UTF-8** option et spécifiez votre encodage préféré.  
  
4.  Choisissez **OK** pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/ source-CharSet (définir jeu de caractères Source)](../../build/reference/source-charset-set-source-character-set.md)   
 [/validate-charset (Valider les caractères compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)