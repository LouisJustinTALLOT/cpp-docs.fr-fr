---
title: Référence de ligne de commande de ML et ML64 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: da3fb143aeaaf6fa8cf31c45b31707fa01bf6898
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057797"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML et référence de ligne de commande ML64
Assemble et des liens d’un ou plusieurs fichiers de code source en langage assembleur. Les options de ligne de commande respectent la casse.  
  
 Pour plus d’informations sur ml64.exe, consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `options`  
 Les options répertoriées dans le tableau suivant.  
  
|Option|Action|  
|------------|------------|  
|**/AT**|Permet la prise en charge du modèle de mémoire minuscule. Active les messages d’erreur pour les constructions de code qui violent la configuration requise pour les fichiers de format .com. Notez que cela n’est pas équivalente à la [. MODÈLE](../../assembler/masm/dot-model.md) **minuscule** directive.<br /><br /> Non disponible dans ml64.exe.|  
|**/Bl** `filename`|Sélectionne un autre éditeur de liens.|  
|**/c**|Assemble uniquement. Ne contient pas de liens.|  
|**/coff**|Génère un type commun d’au format COFF () du fichier objet de module de l’objet. En règle générale requise pour le développement du langage d’assembly Win32.<br /><br /> Non disponible dans ml64.exe.|  
|**/Cp**|Préserve la casse des identificateurs de tous les utilisateurs.|  
|**/CU**|Mappe tous les identificateurs en majuscules (par défaut).<br /><br /> Non disponible dans ml64.exe.|  
|**/Cx**|Préserve la casse dans les symboles publics et extern.|  
|**/D** `symbol`[[=`value`]]|Définit une macro de texte avec le nom donné. Si `value` est manquant, il est vide. Plusieurs jetons séparés par des espaces doivent être entre guillemets.|  
|**/EP**|Génère une liste de sources prétraitées (envoyée vers STDOUT). Consultez **/Sf**.|  
|**/ ERRORREPORT** [ **NONE** &AMP;#124; **INVITE** &AMP;#124; **FILE D’ATTENTE** &AMP;#124; **ENVOYER** ]|Si ml.exe ou ml64.exe échoue lors de l’exécution, vous pouvez utiliser **/ERRORREPORT** à envoyer à Microsoft des informations sur ces erreurs internes.<br /><br /> Pour plus d’informations sur **/ERRORREPORT**, consultez [/errorReport (signaler les erreurs du compilateur interne)](../../build/reference/errorreport-report-internal-compiler-errors.md).|  
|**/F** `hexnum`|Définit la taille de la pile `hexnum` octets (cela revient à **/lien/pile**:`number`). La valeur doit être exprimée en notation hexadécimale. Il doit y avoir un espace entre **/F** et `hexnum`.|  
|**/FE** `filename`|Nommer le fichier exécutable.|  
|**/Fl**[[`filename`]]|Génère un listing de code assemblé. Consultez **/Sf**.|  
|**/Fm**[[`filename`]]|Crée un fichier de mappage de l’éditeur de liens.|  
|**/FO** `filename`|Désigne un fichier objet. Pour plus d’informations, reportez-vous à la section Notes.|  
|**/FPi**|Génère des corrections émulateur arithmétique à virgule flottante (langue mixte uniquement).<br /><br /> Non disponible dans ml64.exe.|  
|**/Fr**[[`filename`]]|Génère un fichier .sbr du navigateur source.|  
|**/FR**[[`filename`]]|Génère une forme étendue d’un fichier .sbr du navigateur source.|  
|**/Gc**|Spécifie l’utilisation de la fonction de type Pascal ou FORTRAN appelant et conventions de dénomination. Identique à **OPTION LANGUAGE : PASCAL**.<br /><br /> Non disponible dans ml64.exe.|  
|**/Gd**|Spécifie l’utilisation de la fonction de style C appelant et conventions de dénomination. Identique à **OPTION LANGUAGE : C**.<br /><br /> Non disponible dans ml64.exe.|  
|**/GZ**|Spécifie l’utilisation de la fonction __stdcall appelant et conventions de dénomination.  Identique à **OPTION LANGUAGE : STCALL**.<br /><br /> Non disponible dans ml64.exe.|  
|**/H** `number`|Restreint les noms externes à chiffres significatifs. La valeur par défaut est 31 caractères.<br /><br /> Non disponible dans ml64.exe.|  
|**/help**|Appelle l’aide rapide de l’aide sur ML.|  
|**/I** `pathname`|Chemin d’accès de jeux pour le fichier include. Un maximum de 10 **/I** options est autorisée.|  
|**/nologo**|Supprime les messages pour l’assembly réussie.|  
|**/OMF**|Génère le type de format (OMF) de fichier de module objet du module de l’objet.  **/OMF** implique **/c**; ML.exe ne prend pas en charge la liaison d’objets OMF.<br /><br /> Non disponible dans ml64.exe.|  
|**/Sa**|Active la liste de toutes les informations disponibles.|  
|**/SAFESEH**|Marque l’objet comme ne contenant aucun gestionnaire d’exceptions ou qui contient les gestionnaires d’exceptions qui sont déclarées avec [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> Non disponible dans ml64.exe.|  
|**/Sf**|Ajoute le fichier de liste à la liste de premier passage.|  
|**/SL** `width`|Définit la largeur de ligne de la liste de caractères par ligne source. Plage est comprise entre 60 et 255 ou 0. Valeur par défaut est 0. Identique à [PAGE](../../assembler/masm/page.md) largeur.|  
|**Sn**|Désactive la table de symboles lors de la génération d’une liste.|  
|**/SP** `length`|Définit la longueur de la page de liste de lignes par page source. Plage est comprise entre 10 et 255 ou 0. Valeur par défaut est 0. Identique à [PAGE](../../assembler/masm/page.md) longueur.|  
|**/Ss** `text`|Spécifie le texte de la liste source. Identique à [sous-titre](../../assembler/masm/subtitle.md) texte.|  
|**/St** `text`|Spécifie le titre de la liste de code source. Identique à [titre](../../assembler/masm/title.md) texte.|  
|**/Sx**|Active les conditions false dans la liste.|  
|**/TA** `filename`|Assemble le fichier source dont le nom ne se termine pas avec l’extension .asm.|  
|**/w**|Identique à **/W0/WX**.|  
|**/W** `level`|Définit le niveau d’avertissement, où `level` = 0, 1, 2 ou 3.|  
|**/WX**|Retourne un code d’erreur si des avertissements sont générés.|  
|**/X**|Ignorer le chemin d’environnement INCLUDE.|  
|**/Zd**|Génère des informations de numéro de ligne dans le fichier objet.|  
|**/Zf**|Rend tous les symboles publics.|  
|**/Zi**|Génère des informations CodeView dans le fichier objet.|  
|**/Zm**|Permet de**M510** option pour une compatibilité maximale avec MASM 5.1.<br /><br /> Non disponible dans ml64.exe.|  
|**/Zp**[[`alignment`]]|Compresse les structures sur la limite d’octets spécifié. Le `alignment` peut être 1, 2 ou 4.|  
|**/Zs**|Effectue une vérification de la syntaxe uniquement.|  
|**/?**|Affiche un résumé de la syntaxe de ligne de commande de ML.|  
  
 `filename`  
 Nom du fichier.  
  
 `linkoptions`  
 Les options de liaison.  Consultez [les Options de l’éditeur de liens](../../build/reference/linker-options.md) pour plus d’informations.  
  
## <a name="remarks"></a>Notes  
 Certaines options de ligne de commande pour ML et ML64 sont dépendantes de la sélection élective. Par exemple, étant donné que ML et ML64 peuvent accepter plusieurs **/c** options, n’importe quel correspondant **/Fo** options doivent être spécifiées avant **/c**. L’exemple de ligne de commande suivant illustre une spécification de fichier d’objet pour chaque spécification de fichier d’assembly :  
  
 **ml.exe /Fo a.asm a1.obj /c /Fo b1.obj /c b.asm**  
  
## <a name="environment-variables"></a>Environment Variables  
  
|Variable|Description|  
|--------------|-----------------|  
|INCLUDE|Spécifie le chemin de recherche des fichiers include.|  
|ML|Spécifie les options de ligne de commande par défaut.|  
|TMP|Spécifie le chemin d’accès pour les fichiers temporaires.|  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)   
 [Informations de référence sur Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)