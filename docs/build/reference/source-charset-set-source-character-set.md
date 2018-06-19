---
title: -source-charset (jeu de caractères Source ensemble) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4f010eb0f0b83dbc41ebeff624033e59d582535
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379222"
---
# <a name="source-charset-set-source-character-set"></a>/ source-CharSet (définir Source Character Set)
Permet de spécifier la source jeu de caractères pour votre fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/source-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Arguments  
 **IANA_name**  
 Nom du jeu de caractères définis par l’IANA.  
  
 **CPID**  
 Identificateur de la page de code comme un nombre décimal.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la **/source-CharSet** option pour spécifier un caractère source étendue ensemble à utiliser lors de vos fichiers sources incluent les caractères qui ne sont pas représentés dans le jeu de caractères sources de base. Le jeu de caractères source est l’encodage utilisé pour interpréter le texte de la source de votre programme dans la représentation interne utilisée comme entrée pour les phases de prétraitement avant la compilation. La représentation interne est ensuite convertie au jeu de caractères d’exécution pour stocker des valeurs de chaîne et de caractère dans le fichier exécutable. Vous pouvez utiliser soit l’IANA ou nom de jeu de caractères ISO, ou un point (.) suivi d’un identificateur de page de code décimal de 3 à 5 chiffres pour spécifier le jeu de caractères à utiliser. Pour une liste de prise en charge les identificateurs de page de code et les noms de jeu de caractères, consultez [Code Page Identifiers](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est encodé au format Unicode, par exemple, UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvé, il suppose que le fichier source est encodé à l’aide de la page de code utilisateur actuel, sauf si vous spécifiez un jeu de caractères nom ou page de codes à l’aide de la **/source-CharSet** option. Visual Studio vous permet d’enregistrer votre code source C++ à l’aide de plusieurs codages de caractères. Pour plus d’informations sur les jeux de caractères source et de l’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation de langage.  
  
 Le jeu de caractères source que vous fournissez doit mapper les caractères ASCII 7 bits aux mêmes points de code dans votre jeu de caractères ou de nombreuses erreurs de compilation sont susceptibles d’appliquer. Votre jeu de caractères source doit également être mappable au jeu puissent être codés en UTF-8 de caractères Unicode étendus. Les caractères qui ne sont pas puissent être codés en UTF-8 sont représentés par un remplacement spécifique à l’implémentation. Le compilateur Microsoft utilise un point d’interrogation pour ces caractères.  
  
 Si vous souhaitez définir le jeu de caractères source et le jeu de caractères d’exécution au format UTF-8, vous pouvez utiliser la **/UTF-8** option du compilateur en guise de raccourci. Il revient à spécifier **/source-charset:utf-/execution 8-charset:utf-8** sur la ligne de commande. Une de ces options également permet la **/Validate-CharSet** option par défaut.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration**, **C/C++**, **ligne de commande** dossier.  
  
3.  Dans **Options avancées**, ajoutez le **/source-CharSet** option, puis spécifiez votre encodage préféré.  
  
4.  Choisissez **OK** pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/ UTF-8 (définir la Source et le fichier exécutable jeux de caractères UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset (Valider les caractères compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)