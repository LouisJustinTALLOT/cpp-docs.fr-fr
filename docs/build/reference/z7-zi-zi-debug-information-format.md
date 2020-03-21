---
title: /Z7, /Zi, /ZI (Format des informations de débogage)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: aeaf435874b6d6b9dbc8a3d12ec06d38bf33aaae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078264"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format des informations de débogage)

Spécifie le type d’informations de débogage créées pour votre programme et si ces informations sont conservées dans des fichiers objets ou dans un fichier de base de données du programme (PDB).

## <a name="syntax"></a>Syntaxe

> **/Z**{**7**|**i**|**i**}

## <a name="remarks"></a>Notes

Lorsque le code est compilé et généré en mode débogage, le compilateur produit des noms de symboles pour les fonctions et les variables, les informations de type et les emplacements de numéro de ligne pour une utilisation par le débogueur. Ces informations de débogage symboliques peuvent être incluses dans les fichiers objets (fichiers. obj) produits par le compilateur, ou dans un fichier PDB distinct (fichier. pdb) pour l’exécutable.  Les options de format des informations de débogage sont décrites dans les sections suivantes.

### <a name="none"></a>None

Par défaut, si aucune option de format des informations de débogage n’est spécifiée, le compilateur ne produit aucune information de débogage, de sorte que la compilation est plus rapide.

### <a name="z7"></a>/Z7

L’option **/Z7** produit des fichiers objets qui contiennent également des informations de débogage symboliques complètes à utiliser avec le débogueur. Ces fichiers objets et l’exécutable généré peuvent être beaucoup plus volumineux que les fichiers qui n’ont pas d’informations de débogage. Les informations de débogage symboliques comprennent les noms et types des variables, ainsi que les fonctions et les numéros de ligne. Aucun fichier PDB n’est produit.

Pour les serveurs de distribution de versions Debug de bibliothèques tierces, il existe un avantage de ne pas avoir de fichier PDB. Toutefois, les fichiers objets des en-têtes précompilés sont nécessaires pendant la phase de lien de bibliothèque et pour le débogage. S’il n’existe que des informations de type (et aucun code) dans le fichier objet. pch, vous devez également utiliser l’option [/yl (injecter une référence PCH pour la bibliothèque de débogage)](yl-inject-pch-reference-for-debug-library.md) , qui est activée par défaut lorsque vous générez la bibliothèque.

L’option [/GM (activer la régénération minimale)](gm-enable-minimal-rebuild.md) déconseillée n’est pas disponible quand **/Z7** est spécifié.

### <a name="zi"></a>/ZI

L’option **/Zi** produit un fichier PDB distinct qui contient toutes les informations de débogage symboliques à utiliser avec le débogueur. Les informations de débogage ne sont pas incluses dans les fichiers objets ou l’exécutable, ce qui les rend plus petits.

L’utilisation de **/Zi** n’affecte pas les optimisations. Toutefois, **/Zi** implique **/Debug**; Pour plus d’informations [, consultez/debug (générer des informations de débogage)](debug-generate-debug-info.md) .

Lorsque vous spécifiez à la fois **/Zi** et **/CLR**, l’attribut <xref:System.Diagnostics.DebuggableAttribute> n’est pas placé dans les métadonnées de l’assembly. Si vous le souhaitez, vous devez le spécifier dans le code source. Cet attribut peut affecter les performances d'exécution de l'application. Pour plus d’informations sur la façon dont l’attribut **déboguable** affecte les performances et sur la façon dont vous pouvez modifier l’impact sur les performances, consultez [rendre une image plus facile à déboguer](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Le compilateur nomme le fichier PDB *Project*. pdb. Si vous compilez un fichier en dehors d’un projet, le compilateur crée un fichier PDB nommé VC*x*. pdb, où *x* est une concaténation du numéro de version principale et secondaire de la version du compilateur en cours d’utilisation. Le compilateur incorpore le nom du fichier PDB et une signature avec horodateur d’identification dans chaque fichier objet créé à l’aide de cette option, qui pointe le débogueur vers l’emplacement des informations symboliques et de numéro de ligne. Le nom et la signature dans le fichier PDB doivent correspondre à l’exécutable pour les symboles à charger dans le débogueur. Le débogueur WinDBG peut charger des symboles incompatibles à l’aide de la commande `.symopt+0x40`. Visual Studio ne dispose pas d’une option similaire pour charger des symboles incompatibles.

Si vous créez une bibliothèque à partir d’objets qui ont été compilés à l’aide de **/Zi**, le fichier. pdb associé doit être disponible lorsque la bibliothèque est liée à un programme. Par conséquent, si vous distribuez la bibliothèque, vous devez également distribuer le fichier PDB. Pour créer une bibliothèque qui contient des informations de débogage sans utiliser de fichiers PDB, vous devez sélectionner l’option **/Z7** . Si vous utilisez les options d’en-têtes précompilés, les informations de débogage de l’en-tête précompilé et du reste du code source sont placées dans le fichier PDB.

### <a name="zi"></a>/ZI

L’option **/Zi** est semblable à **/Zi**, mais elle produit un fichier PDB dans un format qui prend en charge la fonctionnalité [Modifier & Continuer](/visualstudio/debugger/edit-and-continue-visual-cpp) . Pour utiliser les fonctionnalités de débogage modifier & continuer, vous devez utiliser cette option. La fonctionnalité Modifier & Continuer est utile pour la productivité des développeurs, mais peut entraîner des problèmes de taille de code, de performances et de conformité du compilateur. Étant donné que la plupart des optimisations ne sont pas compatibles avec modifier & continuer, l’utilisation de **/Zi** désactive toutes les instructions `#pragma optimize` dans votre code. L’option **/Zi** est également incompatible avec l’utilisation de [ &#95; &#95;la&#95; &#95; macro prédéfinie Line](../../preprocessor/predefined-macros.md). le code compilé avec **/Zi** ne peut pas utiliser  **&#95; &#95;&#95; Line** comme argument de modèle sans type, même si **&#95; &#95;Line&#95;** peut être utilisé dans les expansions de macro.

L’option **/Zi** force les options [/Gy (activer la liaison au niveau des fonctions)](gy-enable-function-level-linking.md) et [/FC (chemin d’accès complet du fichier de code source dans les Diagnostics)](fc-full-path-of-source-code-file-in-diagnostics.md) à utiliser dans votre compilation.

**/Zi** n’est pas compatible avec [/clr (compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> L’option **/Zi** est uniquement disponible dans les compilateurs ciblant les processeurs x86 et x64. Cette option du compilateur n’est pas disponible dans les compilateurs ciblant les processeurs ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez les **Propriétés de configuration** > page de propriétés **général** **CC++ /**  > .

1. Modifiez la propriété **format des informations de débogage** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
