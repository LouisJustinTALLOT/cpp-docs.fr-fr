---
title: ML et référence de ligne de commande ML64
ms.date: 08/30/2018
f1_keywords:
- ML
helpviewer_keywords:
- /W* MASM compiler option
- /c MASM compiler option
- /EP MASM compiler option
- /Fe MASM compiler option
- /Zp MASM compiler option
- /AT MASM compiler option
- /Zm MASM compiler option
- /Sf MASM compiler option
- /Sp MASM compiler option
- /w MASM compiler option
- /Fl MASM compiler option
- /coff MASM compiler option
- /St MASM compiler option
- /Cx MASM compiler option
- /Sl MASM compiler option
- /Cu MASM compiler option
- MASM (Microsoft Macro Assembler), ML command-line reference
- /FPi MASM compiler option
- /Zf MASM compiler option
- ML environment variable
- /Fr MASM compiler option
- /help MASM compiler option
- /Sa MASM compiler option
- /Zd MASM compiler option
- /I MASM compiler option
- /? MASM compiler option
- /Bl MASM compiler option
- /Fm MASM compiler option
- /Fo MASM compiler option
- command-line reference [ML]
- /Sn MASM compiler option
- /Gd MASM compiler option
- /D* MASM compiler option
- environment variables, ML
- /Gc MASM compiler option
- /F* MASM compiler option
- /Sc MASM compiler option
- /H MASM compiler option
- /Zs MASM compiler option
- /omf MASM compiler option
- /Sg MASM compiler option
- /Cp MASM compiler option
- /Zi MASM compiler option
- /nologo MASM compiler option
- /Sx MASM compiler option
- /WX MASM compiler option
- /Ss MASM compiler option
- command line, reference [ML]
- /Ta MASM compiler option
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
ms.openlocfilehash: 470cad1be6fe314fde89ee144a8935664ead5953
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397195"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML et référence de ligne de commande ML64

Assemble et lie un ou plusieurs fichiers sources en langage assembleur. Les options de ligne de commande respectent la casse.

Pour plus d’informations sur ml64. exe, consultez [MASM pour x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Syntaxe

> ML \[*options*] *nom de fichier* \[ *options*de \[] *nom de fichier*]
>
> ML64 \[*options*] *filename* \[ *options*\[] *nom de fichier*]... \[/Link *linkoptions*]

### <a name="parameters"></a>Paramètres

*options*\
Les options énumérées dans le tableau suivant.

|Option|Action|
|------------|------------|
|**/AT**|Active la prise en charge des modèles de mémoire minuscules. Active les messages d’erreur pour les constructions de code qui enfreignent les spécifications pour les fichiers de format. com. Notez que cela n’est pas équivalent à [. Directive de modèle](../../assembler/masm/dot-model.md) **Tiny** .<br /><br /> Non disponible dans ml64. exe.|
|*Nom de fichier* /BL|Sélectionne un autre éditeur de liens.|
|**/c**|Assemble uniquement. Ne lie pas.|
|**/COFF**|Génère le type COFF (Common Object File Format) du module objet. Généralement requis pour le développement du langage assembleur Win32.<br /><br /> Non disponible dans ml64. exe.|
|**/CP**|Conserve la casse de tous les identificateurs d’utilisateur.|
|**/Cu**|Mappe tous les identificateurs en majuscules (par défaut).<br /><br /> Non disponible dans ml64. exe.|
|**/CX**|Conserve la casse dans les symboles publics et extern.|
|**/D** *symbol*⟦ =*value*⟧|Définit une macro de texte avec le nom donné. Si la *valeur* est manquante, elle est vide. Plusieurs jetons séparés par des espaces doivent être placés entre guillemets.|
|**/EP**|Génère une liste de sources prétraitées (envoyée à STDOUT). Consultez **/SF**.|
|**/errorreport** [ **aucune** &#124; **invite** &#124; de **file d’attente d'** &#124; **envoi** ]|Si ml. exe ou ml64. exe échoue au moment de l’exécution, vous pouvez utiliser **/errorreport** pour envoyer des informations à Microsoft sur ces erreurs internes.<br /><br /> Pour plus d’informations sur **/errorreport**, consultez [/errorreport (signaler les erreurs internes du compilateur)](../../build/reference/errorreport-report-internal-compiler-errors.md).|
|**/F** *hexnum*|Définit la taille de la pile sur *hexnum* octets (identique à **/Link/Stack**:*Number*). La valeur doit être exprimée en notation hexadécimale. Il doit y avoir un espace entre **/f** et *hexnum*.|
|**/Fe** *nom de fichier*|Nomme le fichier exécutable.|
|**/FL**⟦*nom de fichier*⟧|Génère une liste de code assemblé. Consultez **/SF**.|
|**/FM**⟦*NomFichier*⟧|Crée un fichier de mappage de l’éditeur de liens.|
|**/FO** *nom_fichier*|Nomme un fichier objet. Pour plus d’informations, consultez la section Notes.|
|**/FPi**|Génère des correctifs d’émulateur pour les opérations arithmétiques à virgule flottante (langage mixte uniquement).<br /><br /> Non disponible dans ml64. exe.|
|**/Fr**⟦*filename*⟧|Génère un fichier browser. SBR source.|
|**/Fr**⟦*filename*⟧|Génère une forme étendue d’un fichier. SBR Browser source.|
|**/Gc**|Spécifie l’utilisation des conventions de nommage et d’appel de fonction FORTRAN ou Pascal. Identique à la **langue des options : Pascal**.<br /><br /> Non disponible dans ml64. exe.|
|**/Gd**|Spécifie l’utilisation des conventions d’appel et de nommage des fonctions de style C. Identique à l' **option Language : C**.<br /><br /> Non disponible dans ml64. exe.|
|**/GZ**|Spécifie l’utilisation de __stdcall l’appel de fonction et les conventions d’affectation des noms.  Identique à la **langue des options : STCALL**.<br /><br /> Non disponible dans ml64. exe.|
|**/H** *nombre*|Limite les noms externes aux caractères significatifs. La valeur par défaut est 31 caractères.<br /><br /> Non disponible dans ml64. exe.|
|**/help**|Appelle QuickHelp pour obtenir de l’aide sur ML.|
|**/I** *chemin d’accès*|Définit le chemin d’accès pour le fichier include. Un maximum de 10 options **/i** est autorisé.|
|**/nologo**|Supprime les messages pour la réussite de l’assembly.|
|**/OMF**|Génère le type de module d’objet de format de fichier de module (OMF).  **/OMF** implique **/c**; ML. exe ne prend pas en charge la liaison des objets OMF.<br /><br /> Non disponible dans ml64. exe.|
|**/Sa**|Active la liste de toutes les informations disponibles.|
|**/SAFESEH**|Marque l’objet comme ne contenant aucun gestionnaire d’exceptions ou contenant les gestionnaires d’exceptions qui sont tous déclarés avec [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> Non disponible dans ml64. exe.|
|**/Sf**|Ajoute la liste de première passe au fichier de liste.|
|*Largeur* de/SL|Définit la largeur de ligne de la liste de sources en caractères par ligne. La plage est comprise entre 60 et 255. La valeur par défaut est 0. Identique à la largeur de la [page](../../assembler/masm/page.md) .|
|**/SN**|Désactive la table de symboles lors de la génération d’une liste.|
|*Longueur* /SP|Définit la longueur de page de la liste de sources dans les lignes par page. La plage est comprise entre 10 et 255. La valeur par défaut est 0. Identique à la longueur de la [page](../../assembler/masm/page.md) .|
|**/SS** *texte*|Spécifie le texte de la liste de sources. Identique au texte du [sous-titre](../../assembler/masm/subtitle.md) .|
|*Texte* /St|Spécifie le titre de la liste source. Identique au texte du [titre](../../assembler/masm/title.md) .|
|**/Sx**|Active les fausses affections dans la liste.|
|*Nom de fichier* /ta|Assemble le fichier source dont le nom ne se termine pas par l’extension. asm.|
|**/w**|Identique à **/W0/WX**.|
|*Niveau* /w|Définit le niveau d’avertissement, où *Level* = 0, 1, 2 ou 3.|
|**/WX**|Retourne un code d’erreur si des avertissements sont générés.|
|**/X**|Ignorer le chemin d’accès de l’environnement INCLUDe.|
|**/Zd**|Génère des informations de numéro de ligne dans le fichier objet.|
|**/ZF**|Rend tous les symboles publics.|
|**/Zi**|Génère des informations CodeView dans le fichier objet.|
|**/Zm**|Active l’option**M510** pour une compatibilité maximale avec MASM 5,1.<br /><br /> Non disponible dans ml64. exe.|
|*Alignement* **⟦ ⟧**|Compresse les structures sur la limite d’octets spécifiée. L' *alignement* peut être 1, 2 ou 4.|
|**/Zs**|Effectue une vérification de la syntaxe uniquement.|
|**/?**|Affiche un résumé de la syntaxe de la ligne de commande ML.|

*nom de fichier*\
Nom du fichier.

*linkoptions*\
Options de lien.  Pour plus d’informations, consultez Options de l' [éditeur de liens](../../build/reference/linker-options.md) .

## <a name="remarks"></a>Notes

Certaines options de ligne de commande pour ML et ML64 sont sensibles au positionnement. Par exemple, étant donné que ML et ML64 peuvent accepter plusieurs options **/c** , toutes les options **/FO** correspondantes doivent être spécifiées avant **/c**. L’exemple de ligne de commande suivant illustre une spécification de fichier objet pour chaque spécification de fichier d’assembly :

**ml. exe/FO a1. obj/c a. asm/FO B1. obj/c b. asm**

## <a name="environment-variables"></a>Environment Variables

|Variable|Description|
|--------------|-----------------|
|INCLUDE|Spécifie le chemin de recherche des fichiers include.|
|ML|Spécifie les options de ligne de commande par défaut.|
|TMP|Spécifie le chemin d’accès des fichiers temporaires.|

## <a name="see-also"></a>Voir aussi

[Millilitres de messages d’erreur](../../assembler/masm/ml-error-messages.md)\
[Informations de référence sur Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)
