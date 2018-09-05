---
title: Référence de ligne de commande ML64 et ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ML
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41d3603bc09b7c63fdd152e1c7d5921c2bb3eb7c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693401"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML et référence de ligne de commande ML64

Assemble et des liens d’un ou plusieurs fichiers de code source en langage assembleur. Les options de ligne de commande respectent la casse.

Pour plus d’informations sur ml64.exe, consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Syntaxe

> ML [[*options*]] *filename* [[[[*options*]] *filename*]]

> Ml64 [[*options*]] *filename* [[[[*options*]] *filename*]]... [[/ link, *linkoptions*]]

### <a name="parameters"></a>Paramètres

*options*<br/>
Les options répertoriées dans le tableau suivant.

|Option|Action|
|------------|------------|
|**/AT**|Permet la prise en charge du modèle de mémoire minuscule. Permet de messages d’erreur pour les constructions de code qui violent la configuration requise pour les fichiers de format de .com. Notez que cela n’est pas équivalente à la [. MODÈLE](../../assembler/masm/dot-model.md) **TINY** directive.<br /><br /> Non disponible dans ml64.exe.|
|**/BI** *nom de fichier*|Sélectionne un autre éditeur de liens.|
|**/c**|Assemble uniquement. Ne contient pas de liens.|
|**/coff**|Génère un type commun d’au format COFF () du fichier objet de module de l’objet. En règle générale requise pour le développement du langage d’assembly Win32.<br /><br /> Non disponible dans ml64.exe.|
|**/Cp**|Préserve la casse de tous les identificateurs d’utilisateur.|
|**/CU**|Mappe tous les identificateurs en majuscules (par défaut).<br /><br /> Non disponible dans ml64.exe.|
|**/Cx**|Préserve la casse dans les symboles publics et extern.|
|**/D** *symbole*[[=*valeur*]]|Définit une macro de texte portant le nom spécifié. Si *valeur* est manquant, il est vide. Plusieurs jetons séparés par des espaces doivent être entourés de guillemets.|
|**/EP**|Génère une liste de source prétraité (envoyée vers STDOUT). Consultez **/Sf**.|
|**/ ERRORREPORT** [ **NONE** &AMP;#124; **INVITE** &AMP;#124; **FILE D’ATTENTE** &AMP;#124; **ENVOYER** ]|Si ml.exe ou ml64.exe échoue lors de l’exécution, vous pouvez utiliser **/ERRORREPORT** pour envoyer des informations à Microsoft concernant ces erreurs internes.<br /><br /> Pour plus d’informations sur **/ERRORREPORT**, consultez [/errorReport (signaler les erreurs du compilateur interne)](../../build/reference/errorreport-report-internal-compiler-errors.md).|
|**/F** *hexnum*|Taille de pile de jeux *hexnum* octets (Ceci est le même que **/lien/STACK**:*nombre*). La valeur doit être exprimée en notation hexadécimale. Il doit y avoir un espace entre **/F** et *hexnum*.|
|**/Fe** *nom de fichier*|Nomme le fichier exécutable.|
|**/Fl**[[*filename*]]|Génère un listing de code assemblé. Consultez **/Sf**.|
|**/FM**[[*filename*]]|Crée un fichier de mappage de l’éditeur de liens.|
|**/Fo** *nom de fichier*|Désigne un fichier objet. Consultez la section Notes pour plus d’informations.|
|**/FPi**|Génère des correctifs d’émulateur pour l’arithmétique à virgule flottante (langue mixte uniquement).<br /><br /> Non disponible dans ml64.exe.|
|**/Fr**[[*filename*]]|Génère un fichier .sbr du navigateur source.|
|**/FR**[[*filename*]]|Génère une forme étendue d’un fichier .sbr du navigateur source.|
|**/Gc**|Spécifie l’utilisation de la fonction de type Pascal ou FORTRAN appelant et conventions de dénomination. Identique à **OPTION LANGUAGE : PASCAL**.<br /><br /> Non disponible dans ml64.exe.|
|**/Gd**|Spécifie l’utilisation de la fonction de style C appelant et conventions de dénomination. Identique à **OPTION LANGUAGE : C**.<br /><br /> Non disponible dans ml64.exe.|
|**/GZ**|Spécifie l’utilisation de la fonction __stdcall appelant et conventions de dénomination.  Identique à **OPTION LANGUAGE : STCALL**.<br /><br /> Non disponible dans ml64.exe.|
|**/H** *nombre*|Restreint les noms externes à nombre caractères significatifs. La valeur par défaut est 31 caractères.<br /><br /> Non disponible dans ml64.exe.|
|**/help**|Appelle l’aide rapide de l’aide sur ML.|
|**/I** *chemin d’accès*|Chemin d’accès de jeux pour le fichier include. Un maximum de 10 **/I** options est autorisée.|
|**/nologo**|Supprime les messages pour l’assembly réussie.|
|**/OMF**|Génère le type de format (OMF) de fichier de module objet du module de l’objet.  **/OMF** implique **/c**; ML.exe ne prend pas en charge la liaison des objets OMF.<br /><br /> Non disponible dans ml64.exe.|
|**/Sa**|Active la liste de toutes les informations disponibles.|
|**/SAFESEH**|Marque l’objet comme ne contenant aucun gestionnaire d’exceptions ou contenant des gestionnaires d’exceptions qui sont déclarées avec [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> Non disponible dans ml64.exe.|
|**/Sf**|Ajoute un fichier de liste de listing de premier passage.|
|**/SL** *la largeur*|Définit la largeur de ligne de la liste de caractères par ligne source. Plage est comprise entre 60 et 255 ou 0. Valeur par défaut est 0. Identique à [PAGE](../../assembler/masm/page.md) la largeur.|
|**/Sn**|Désactive la table de symboles lors de la génération d’une liste.|
|**/SP** *longueur*|Définit la longueur de la page de liste en lignes par page source. Plage est comprise entre 10 et 255 ou 0. Valeur par défaut est 0. Identique à [PAGE](../../assembler/masm/page.md) longueur.|
|**/Ss** *texte*|Spécifie le texte pour la liste source. Identique à [sous-titre](../../assembler/masm/subtitle.md) texte.|
|**/St** *texte*|Spécifie le titre de la liste de source. Identique à [titre](../../assembler/masm/title.md) texte.|
|**/Sx**|Active les conditions false dans la liste.|
|**/TA** *nom de fichier*|Assemble le fichier source dont le nom ne se termine pas avec l’extension .asm.|
|**/w**|Identique à **/W0/WX**.|
|**/W** *niveau*|Définit le niveau d’avertissement, où *niveau* = 0, 1, 2 ou 3.|
|**/WX**|Retourne un code d’erreur si des avertissements sont générés.|
|**/X**|Ignorer le chemin d’environnement INCLUDE.|
|**/Zd**|Génère des informations de numéro de ligne dans un fichier objet.|
|**/Zf**|Rend tous les symboles publics.|
|**/Zi**|Génère des informations CodeView dans le fichier objet.|
|**/Zm**|Permet de**M510** option pour optimiser la compatibilité avec MASM 5.1.<br /><br /> Non disponible dans ml64.exe.|
|**/Zp**[[*alignement*]]|Compresse les structures sur la limite d’octet spécifié. Le *alignement* peut être 1, 2 ou 4.|
|**/Zs**|Effectue une vérification de la syntaxe uniquement.|
|**/?**|Affiche un résumé de syntaxe de ligne de commande ML.|

*filename*<br/>
Nom du fichier.

*linkoptions*<br/>
Les options de lien.  Consultez [les Options de l’éditeur de liens](../../build/reference/linker-options.md) pour plus d’informations.

## <a name="remarks"></a>Notes

Certaines options de ligne de commande pour ML64 et ML sont dépendantes de la sélection élective. Par exemple, étant donné que ML64 et ML peuvent accepter plusieurs **/c** options, n’importe quel correspondant **/Fo** options doivent être spécifiées avant **/c**. L’exemple de ligne de commande suivant illustre une spécification de fichier d’objet pour chaque spécification de fichier d’assembly :

**ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**

## <a name="environment-variables"></a>Environment Variables

|Variable|Description|
|--------------|-----------------|
|INCLUDE|Spécifie le chemin de recherche des fichiers include.|
|ML|Spécifie les options de ligne de commande par défaut.|
|TMP|Spécifie le chemin d’accès pour les fichiers temporaires.|

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>
[Informations de référence sur Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>