---
description: 'En savoir plus sur : options du compilateur et de l’éditeur de liens (C++/CX)'
title: Options du compilateur et de l'éditeur de liens (C++/CX)
ms.date: 01/22/2017
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
ms.openlocfilehash: 66f3cf5a08d7ca0a07b5708495f76902c2286436
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340422"
---
# <a name="compiler-and-linker-options-ccx"></a>Options du compilateur et de l'éditeur de liens (C++/CX)

Une variable d’environnement, les options du compilateur C++/CX et les options de l’éditeur de liens prennent en charge la génération d’applications pour le Windows Runtime.

## <a name="library-path"></a>Chemin de la bibliothèque

La variable d’environnement %LIBPATH% spécifie le chemin par défaut pour rechercher des fichiers .winmd.

## <a name="compiler-options"></a>Options du compilateur

|Option|Description|
|------------|-----------------|
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|Active Windows Runtime extensions de langage.<br /><br /> Le paramètre `nostdlib` empêche le compilateur d’utiliser le chemin de recherche standard, prédéfini pour rechercher des fichiers d’assembly et .winmd.<br /><br /> L’option de compilateur **/ZW** spécifie implicitement les options de compilateur suivantes :<br /><br />- **/FI** vccorlib.h, qui force l’inclusion du fichier d’en-tête vccorlib.h définissant plusieurs types demandés par le compilateur.<br />- [/Fu](../build/reference/fu-name-forced-hash-using-file.md) Windows. winmd, qui force l’inclusion du fichier de métadonnées Windows. winmd fourni par le système d’exploitation et définit de nombreux types dans le Windows Runtime.<br />- **/FU** Platform.winmd, qui force l’inclusion du fichier de métadonnées Platform.winmd fourni par le compilateur, et définit la plupart des types dans la gamme de plateformes d’espaces de noms.|
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Ajoute un répertoire, spécifié par le paramètre *dir* , au chemin de recherche utilisé par le compilateur pour rechercher des fichiers d’assembly et .winmd.|
|**/FU**  *fichier*|Force l’inclusion du module spécifié ou du fichier .winmd. Autrement dit, vous n’êtes pas obligé de spécifier `#using` le *fichier* dans votre code source. Le compilateur force automatiquement l’inclusion de son propre fichier de métadonnées Windows, Platform.winmd.|
|/D "WINAPI_FAMILY=2"|Crée une définition qui permet d’utiliser un sous-ensemble du kit de développement logiciel (SDK) Win32 qui est compatible avec le Windows Runtime.|

## <a name="linker-options"></a>Options de l’éditeur de liens

|Option|Description|
|------------|-----------------|
|/APPCONTAINER[:NO]|Marque le fichier exécutable comme exécutable dans l’appcontainer (uniquement).|
|/WINMD [ : {NO&#124;ONLY}]|Émet un fichier .winmd et un fichier binaire associé. Cette option doit être passée à l’éditeur de liens pour qu’un .winmd soit émis.<br /><br /> **NO**: ne produit pas de fichier .winmd, mais produit un fichier binaire.<br /><br /> **ONLY**: produit un fichier .winmd, mais ne produit pas de fichier binaire.|
|/WINMDFILE:*nom_fichier*|Nom du fichier .winmd à émettre, au lieu du nom du fichier .winmd par défaut. Si plusieurs noms de fichier sont spécifiés sur la ligne de commande, le dernier nom est utilisé.|
|/WINMDDELAYSIGN[:NO]|Signe partiellement le fichier .winmd et place la clé publique dans le fichier binaire.<br /><br /> **NO**: (par défaut) ne signe pas le fichier .winmd.<br /><br /> /WINMDDELAYSIGN n’a aucun effet à moins de spécifier également /WINMDKEYFILE ou /WINMDKEYCONTAINER.|
|/WINMDKEYCONTAINER:*nom*|Spécifie un conteneur de clé pour signer un assembly. Le paramètre *nom* correspond au conteneur de clé qui est utilisé pour signer le fichier de métadonnées.|
|/WINMDKEYFILE:*nom_fichier*|Spécifie une clé ou une paire de clés pour signer l’assembly. Le paramètre *nom_fichier* correspond au conteneur de clé qui est utilisé pour signer le fichier de métadonnées.|

### <a name="remarks"></a>Notes

Quand vous utilisez **/ZW**, le compilateur effectue automatiquement la liaison à la version DLL de C Runtime (CRT). La liaison à la version de la bibliothèque statique n’est pas autorisée et toute utilisation de fonctions CRT qui ne sont pas autorisées dans un plateforme Windows universelle application entraîne une erreur au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Création d’applications et de bibliothèques](../cppcx/building-apps-and-libraries-c-cx.md)
