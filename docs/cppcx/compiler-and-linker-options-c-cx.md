---
title: Options du compilateur et de l'éditeur de liens (C++/CX)
ms.date: 01/22/2017
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
ms.openlocfilehash: cc1964c57d6700995bb283c245e4c63c8e9e313b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383358"
---
# <a name="compiler-and-linker-options-ccx"></a>Options du compilateur et de l'éditeur de liens (C++/CX)

Une variable d’environnement + C, c++ / CX du compilateur et l’éditeur de liens prennent en charge la création d’applications pour l’exécution de Windows.

## <a name="library-path"></a>Chemin de la bibliothèque

La variable d’environnement %LIBPATH% spécifie le chemin par défaut pour rechercher des fichiers .winmd.

## <a name="compiler-options"></a>Options du compilateur

|Option|Description|
|------------|-----------------|
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|Active les extensions de langage Windows Runtime.<br /><br /> Le paramètre `nostdlib` empêche le compilateur d’utiliser le chemin de recherche standard, prédéfini pour rechercher des fichiers d’assembly et .winmd.<br /><br /> L’option de compilateur **/ZW** spécifie implicitement les options de compilateur suivantes :<br /><br />- **/FI** vccorlib.h, qui force l’inclusion du fichier d’en-tête vccorlib.h définissant plusieurs types demandés par le compilateur.<br />- [/FU](../build/reference/fu-name-forced-hash-using-file.md) Windows.winmd, qui force l’inclusion du fichier de métadonnées Windows.winmd fourni par le système d’exploitation, et définit plusieurs types dans le Runtime de Windows.<br />- **/FU** Platform.winmd, qui force l’inclusion du fichier de métadonnées Platform.winmd fourni par le compilateur, et définit la plupart des types dans la gamme de plateformes d’espaces de noms.|
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Ajoute un répertoire, spécifié par le paramètre *dir* , au chemin de recherche utilisé par le compilateur pour rechercher des fichiers d’assembly et .winmd.|
|**/FU**  *fichier*|Force l’inclusion du module spécifié ou du fichier .winmd. Autrement dit, il est inutile de spécifier `#using` *fichier* dans votre code source. Le compilateur force automatiquement l’inclusion de son propre fichier de métadonnées Windows, Platform.winmd.|
|/D "WINAPI_FAMILY=2"|Crée une définition qui permet d’utiliser un sous-ensemble du SDK Win32 compatible avec le Runtime de Windows.|

## <a name="linker-options"></a>Options de l’éditeur de liens

|Option|Description|
|------------|-----------------|
|/APPCONTAINER[:NO]|Marque le fichier exécutable comme exécutable dans l’appcontainer (uniquement).|
|/WINMD[:{NO&#124;ONLY}]|Émet un fichier .winmd et un fichier binaire associé. Cette option doit être passée à l’éditeur de liens pour qu’un .winmd soit émis.<br /><br /> **NO**: ne produit pas de fichier .winmd, mais produit un fichier binaire.<br /><br /> **ONLY**: produit un fichier .winmd, mais ne produit pas de fichier binaire.|
|/WINMDFILE:*nom_fichier*|Nom du fichier .winmd à émettre, au lieu du nom du fichier .winmd par défaut. Si plusieurs noms de fichier sont spécifiés sur la ligne de commande, le dernier nom est utilisé.|
|/WINMDDELAYSIGN[:NO]|Signe partiellement le fichier .winmd et place la clé publique dans le fichier binaire.<br /><br /> **NO**: (par défaut) ne signe pas le fichier .winmd.<br /><br /> /WINMDDELAYSIGN n’a aucun effet à moins de spécifier également /WINMDKEYFILE ou /WINMDKEYCONTAINER.|
|/WINMDKEYCONTAINER:*nom*|Spécifie un conteneur de clé pour signer un assembly. Le paramètre *nom* correspond au conteneur de clé qui est utilisé pour signer le fichier de métadonnées.|
|/WINMDKEYFILE:*nom_fichier*|Spécifie une clé ou une paire de clés pour signer l’assembly. Le paramètre *nom_fichier* correspond au conteneur de clé qui est utilisé pour signer le fichier de métadonnées.|

### <a name="remarks"></a>Notes

Quand vous utilisez **/ZW**, le compilateur effectue automatiquement la liaison à la version DLL de C Runtime (CRT). Liaison avec la version de la bibliothèque statique n’est pas autorisée, et toute utilisation de fonctions CRT qui ne sont pas autorisés dans une application de plateforme Windows universelle entraîne une erreur de compilation.

## <a name="see-also"></a>Voir aussi

[Génération d'applications et de bibliothèques](../cppcx/building-apps-and-libraries-c-cx.md)
