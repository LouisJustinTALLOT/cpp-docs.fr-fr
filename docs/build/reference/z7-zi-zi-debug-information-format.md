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
ms.openlocfilehash: e809c7af7465cde98db11eac8628b76d04f7e8b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316286"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format des informations de débogage)

Spécifie le type d’informations de débogage créées pour votre programme et si ces informations sont conservées dans des fichiers objets ou dans un fichier du programme (PDB) de la base de données.

## <a name="syntax"></a>Syntaxe

> **/Z**{**7**|**i**|**I**}

## <a name="remarks"></a>Notes

Lorsque le code est compilé et généré en mode débogage, le compilateur génère des noms de symboles pour les fonctions et les variables, les informations de type et les emplacements de numéro de ligne pour une utilisation par le débogueur. Ces informations symboliques de débogage peuvent être incluses dans les fichiers objets (fichiers .obj) produits par le compilateur, ou dans un fichier PDB (fichier .pdb) distinct pour le fichier exécutable.  Les options de format des informations de débogage sont décrits dans les sections suivantes.

### <a name="none"></a>Aucun.

Par défaut, si aucune option de format d’informations de débogage est spécifiée, le compilateur ne génère aucune information de débogage, d'où une compilation plus rapide.

### <a name="z7"></a>/Z7

Le **/Z7** option produit des fichiers objets qui contiennent également des informations de débogage symboliques complètes pour une utilisation avec le débogueur. Ces fichiers de l’objet et le fichier exécutable généré peuvent être beaucoup plus important que les fichiers qui ne possèdent aucune information de débogage. Les informations de débogage symboliques comprennent les noms et types des variables, ainsi que les fonctions et les numéros de ligne. Aucun fichier PDB est produit.

Pour les serveurs de distribution des versions debug des bibliothèques tierces, il est l’avantage de ne pas avoir un fichier PDB. Toutefois, les fichiers objets pour tous les en-têtes précompilés sont nécessaires pendant la phase de liaison de bibliothèque et pour le débogage. Si type uniquement des informations (et aucun code) dans le fichier d’objet .pch, vous devez également utiliser le [/Yl (injecter une référence PCH pour une bibliothèque de débogage)](yl-inject-pch-reference-for-debug-library.md) option, qui est activée par défaut, lorsque vous générez la bibliothèque.

Déconseillées [/Gm (activer la régénération minimale)](gm-enable-minimal-rebuild.md) option n’est pas disponible lorsque **/Z7** est spécifié.

### <a name="zi"></a>/ZI

Le **/Zi** option génère un fichier PDB distinct qui contient toutes les informations de débogage symboliques à utiliser avec le débogueur. Les informations de débogage ne sont pas incluses dans les fichiers objets ou exécutable, ce qui les rend beaucoup plus petite.

Utilisation de **/Zi** n’affecte pas les optimisations. Toutefois, **/Zi** implique **/debug**; consultez [/DEBUG (Generate Debug Info)](debug-generate-debug-info.md) pour plus d’informations.

Lorsque vous spécifiez à la fois **/Zi** et **/CLR**, le <xref:System.Diagnostics.DebuggableAttribute> attribut n’est pas placé dans les métadonnées d’assembly. Si vous le souhaitez, vous devez le spécifier dans le code source. Cet attribut peut affecter les performances d'exécution de l'application. Pour plus d’informations sur la façon dont **attribut Debuggable** attribut affecte les performances et la manière dont vous pouvez modifier l’impact sur les performances, consultez [simplification une Image de débogage](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Le compilateur nomme le fichier PDB *projet*.pdb. Si vous compilez un fichier en dehors d’un projet, le compilateur crée un fichier PDB nommé VC*x*.pdb, où *x* est une concaténation du numéro de version majeure et mineure de la version du compilateur en cours d’utilisation. Le compilateur incorpore le nom de fichier PDB et une identification signature horodatés dans chaque fichier objet créé à l’aide de cette option, qui pointe le débogueur à l’emplacement des informations symboliques et le numéro de ligne. Le nom et la signature dans le fichier PDB doivent correspondre à l’exécutable pour les symboles à charger dans le débogueur. Le débogueur WinDBG peut charger des symboles qui ne correspondent pas à l’aide de la `.symopt+0x40` commande. Visual Studio n’a pas une option similaire pour charger des symboles qui ne correspondent pas.

Si vous créez une bibliothèque à partir d’objets qui ont été compilés à l’aide de **/Zi**, le fichier .pdb associé doit être disponible lorsque la bibliothèque est liée à un programme. Par conséquent, si vous distribuez la bibliothèque, vous devez également distribuer le fichier PDB. Pour créer une bibliothèque qui contient des informations de débogage sans utiliser de fichiers PDB, vous devez sélectionner le **/Z7** option. Si vous utilisez les options d’en-têtes précompilés, informations de débogage pour l’en-tête précompilé et le reste du code source sont placée dans le fichier PDB.

### <a name="zi"></a>/ZI

Le **/Zi** option est similaire à **/Zi**, mais il génère un fichier PDB dans un format qui prend en charge la [Modifier & Continuer](/visualstudio/debugger/edit-and-continue-visual-cpp) fonctionnalité. Pour utiliser les fonctionnalités de débogage Modifier & Continuer, vous devez utiliser cette option. La fonctionnalité Modifier & Continuer est utile pour la productivité des développeurs, mais peut entraîner des problèmes dans le code du compilateur, les performances et la taille de la mise en conformité. Étant donné que la plupart des optimisations sont incompatibles avec Modifier & Continuer, à l’aide **/Zi** désactive toutes `#pragma optimize` instructions dans votre code. Le **/Zi** option est également incompatible avec utilisation de la [ &#95; &#95;ligne&#95; &#95; la macro prédéfinie](../../preprocessor/predefined-macros.md); le code compilé avec **/Zi** ne pouvez pas utiliser **&#95; &#95;Ligne&#95; &#95;** comme argument de modèle sans type, bien que **&#95; &#95;ligne&#95; &#95;** peut être utilisé dans les expansions de macros.

Le **/Zi** option force à la fois le [/Gy (activer la liaison au niveau des fonctions)](gy-enable-function-level-linking.md) et [/FC (complet chemin d’accès du fichier de Code Source dans les Diagnostics)](fc-full-path-of-source-code-file-in-diagnostics.md) options à utiliser dans votre compilation.

**/ Zi** n’est pas compatible avec [/clr (Compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> Le **/Zi** option est uniquement disponible dans les compilateurs qui ciblent des processeurs x86 et x64 ; cette option du compilateur n’est pas disponible dans les compilateurs ciblant les processeurs ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez le **propriétés de Configuration** > **C/C++** > **général** page de propriétés.

1. Modifier le **Format des informations de débogage** propriété. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

