---
title: -exécution-charset (définir le jeu de caractères d’exécution) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02f3e4273e9fc4064b26c6e32d708c4e6d586ae1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212670"
---
# <a name="execution-charset-set-execution-character-set"></a>/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)
Vous permet de spécifier l’exécution du jeu de caractères pour votre fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/execution-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Arguments  
 **IANA_name**  
 Nom du jeu de caractères défini par l’IANA.  
  
 **CPID**  
 Identificateur de la page de codes.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la **/Execution-CharSet** option pour spécifier un jeu de caractères d’exécution. Le jeu de caractères d’exécution est l’encodage utilisé pour le texte de votre programme est entrée dans la phase de compilation une fois toutes les étapes de prétraitement. Ce jeu de caractères est utilisé pour la représentation interne de chaînes ou caractères littéraux dans le code compilé. Définissez cette option pour spécifier le jeu de caractères de l’exécution étendue à utiliser lors de vos fichiers sources incluent des caractères qui ne sont pas représentables dans le jeu de caractères d’exécution de base. Vous pouvez utiliser soit l’IANA ou nom de jeu de caractères ISO ou un point (.) suivi d’un identificateur de page de code décimal de 3 à 5 chiffres pour spécifier le jeu de caractères à utiliser. Pour une liste de prise en charge les identificateurs de page de code et les noms de jeu de caractères, consultez [Code Page Identifiers](/windows/desktop/Intl/code-page-identifiers).  
  
 Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est encodé au format Unicode, par exemple, UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvé, il part du principe que le fichier source est encodé à l’aide de la page de codes utilisateur actuel, sauf si vous avez spécifié un jeu de caractères nom ou page de codes à l’aide de la **/source-CharSet** option ou   **/UTF-8** option. Visual Studio vous permet d’enregistrer votre code source C++ à l’aide des plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage.  
  
 Si vous souhaitez définir le jeu de caractères source et le jeu de caractères d’exécution au format UTF-8, vous pouvez utiliser la **/UTF-8** option du compilateur sous forme de raccourci. Il est équivalent à la spécification **/source-charset:utf-/execution 8-charset:utf-8** sur la ligne de commande. Aucune de ces options également permet la **/Validate-CharSet** option par défaut.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration**, **C/C++**, **ligne de commande** dossier.  
  
3.  Dans **Options avancées**, ajoutez le **/Execution-CharSet** option et spécifiez votre encodage préféré.  
  
4.  Choisissez **OK** pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/ source-CharSet (définir jeu de caractères Source)](../../build/reference/source-charset-set-source-character-set.md)   
 [/ UTF-8 (définir la Source et le fichier exécutable jeux de caractères UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset (Valider les caractères compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)