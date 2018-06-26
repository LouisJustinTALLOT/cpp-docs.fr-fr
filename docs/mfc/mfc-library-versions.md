---
title: Versions de bibliothèque MFC | Documents Microsoft
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92568f61bb1ea219ab3ddc96f4c4687dec157c9a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931763"
---
# <a name="mfc-library-versions"></a>Versions de bibliothèque MFC

La bibliothèque MFC est disponible dans les versions qui prennent en charge ANSI sur un octet et du jeu de caractères multioctets (MBCS) code, ainsi que les versions qui prennent en charge Unicode (codé en UTF-16LE, le jeu de caractères natif de Windows). Chaque version MFC est disponible sous la forme d’une bibliothèque statique ou une DLL partagée. Il existe également une version de bibliothèque statique MFC plus petite qui omet les contrôles MFC pour les boîtes de dialogue, pour les applications qui sont très sensibles à la taille et n’avez pas besoin de ces contrôles. Les bibliothèques MFC sont disponibles dans les versions debug et release de versions pour les architectures prises en charge qui incluent x86, x64 et les processeurs ARM. Vous pouvez créer les deux applications (fichiers .exe) et les DLL avec n’importe quelle version des bibliothèques MFC. Il existe également un ensemble de bibliothèques MFC compilés pour l’interface avec le code managé. DLL MFC partagées incluent un numéro de version pour indiquer la compatibilité binaire des bibliothèques.

## <a name="automatic-linking-of-mfc-library-versions"></a>Liaison automatique de versions de bibliothèque MFC

Les fichiers d’en-tête MFC déterminent automatiquement la version correcte de la bibliothèque MFC à lier, en fonction des valeurs définies dans votre environnement de génération. Les fichiers d’en-tête MFC ajoutent les directives du compilateur indiquant à l’éditeur de liens à lier dans une version spécifique de la bibliothèque MFC.

Par exemple, le AFX. H demande à l’éditeur de liens à lier dans la complète statique, limitée statique ou partagée version DLL de MFC ; Version ANSI/MBCS ou Unicode ; et la version de débogage ou de la vente au détail, selon votre configuration de build :

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

Fichiers d’en-tête MFC incluent également des directives à lier dans toutes les bibliothèques requises, y compris les bibliothèques MFC, bibliothèques Win32, les bibliothèques OLE, les bibliothèques OLE créées à partir d’exemples, les bibliothèques ODBC et ainsi de suite. 

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS et Unicode

Les versions de la bibliothèque MFC ANSI/MBCS prennent en charge les deux jeux de caractères codés par exemple ASCII et jeux de caractères multioctets telles que Shift-JIS. Les versions de la bibliothèque MFC Unicode prennent en charge Unicode dans sa forme de codé en UTF-16LE caractères larges. Utilisez les versions de bibliothèque ANSI/MBCS de MFC pour la prise en charge Unicode d’encodées UTF-8.

Pour définir la configuration de votre projet à utiliser sur un octet, multioctet ou les caractères larges chaînes et caractères prise en charge Unicode dans l’IDE, utilisez le **propriétés du projet** boîte de dialogue. Dans le **propriétés de Configuration** > **général** , définissez le **du jeu de caractères** propriété **pas définir** à utiliser un jeu de caractères d’un octet. Affectez à la propriété **utiliser un jeu de caractères codés sur plusieurs octets** à utiliser un jeu de caractères multioctets ou **utiliser un jeu de caractères Unicode** d’utiliser Unicode encodé en UTF-16.

Projets MFC utilisent le symbole de préprocesseur \_pour indiquer la prise en charge de Unicode UTF-16 caractères larges, UNICODE et \_prise en charge MBCS pour indiquer MBCS. Ces options s’excluent mutuellement dans un projet.

## <a name="mfc-static-library-naming-conventions"></a>Conventions d’affectation de noms de bibliothèque statique MFC

Bibliothèques statiques MFC utilisent les conventions d’affectation de noms suivantes. Les noms de bibliothèque ont la forme

> *u*AFX*c ** d*. LIB

où les lettres affichés en italique minuscules sont des espaces réservés pour des spécificateurs dont la signification est indiquée dans le tableau suivant :

|Spécificateur|Valeurs et significations|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) ou Unicode (U) ; ne spécifiez pas de version sans contrôles MFC dans les boîtes de dialogue|
|*c*|Version avec des contrôles MFC dans les boîtes de dialogue (PA) ou sans (NMCD)|
|*d*|Debug ou Release : D = Debug ; omettez le spécificateur de version|

Toutes les bibliothèques répertoriées dans le tableau suivant sont incluses prégénérées dans le répertoire \atlmfc\lib pour les architectures de build pris en charge.

|Bibliothèque|Description|
|-------------|-----------------|
|NAFXCW.LIB|Bibliothèque de liaison statique MFC, version Release|
|NAFXCWD.LIB|Bibliothèque de liaison statique MFC, version de débogage|
|UAFXCW.LIB|Bibliothèque de liaison statique MFC avec prise en charge d’Unicode, version Release|
|UAFXCWD. LIB|Bibliothèque de liaison statique MFC avec prise en charge d’Unicode, version de débogage|
|AFXNMCD.LIB|Bibliothèque de liaison statique MFC sans contrôles de boîte de dialogue MFC, version Release|
|AFXNMCDD. LIB|Bibliothèque de liaison statique MFC sans contrôles de boîte de dialogue MFC, version de débogage|

Fichiers du débogueur qui ont le même nom et une extension .pdb sont également disponibles pour chacune des bibliothèques statiques.

## <a name="mfc-shared-dll-naming-conventions"></a>Conventions d’affectation de noms de DLL partagée de MFC

La bibliothèque MFC DLL partagées également suivent une convention d’affectation de noms structurée. Cela rend plus facile de savoir quelle DLL ou la bibliothèque, vous devez utiliser à cette fin.

La DLL de MFC ont *version* des nombres qui indiquent la compatibilité binaire. Utilisez les DLL MFC qui ont la même version que d’autres bibliothèques et ensemble d’outils du compilateur de garantir la compatibilité d’un projet.

|DLL|Description|
|---------|-----------------|
|MFC*version*. DLL|Version DLL MFC, ANSI ou MBCS version|
|MFC*version*U.DLL|DLL MFC, version Release d’Unicode|
|MFC*version*D.DLL|Version DLL MFC, ANSI ou MBCS de débogage|
|MFC*version*UD. DLL|DLL MFC, version Unicode Debug|
|MFCM*version*. DLL|DLL MFC avec les contrôles Windows Forms, version ANSI ou d’une version de MBCS|
|MFCM*version*U.DLL|DLL MFC avec les contrôles Windows Forms, version Release d’Unicode|
|MFCM*version*D.DLL|DLL MFC avec les contrôles Windows Forms, version ANSI ou MBCS de débogage|
|MFCM*version*UD. DLL|DLL MFC avec les contrôles Windows Forms, version Unicode Debug|

Les bibliothèques d’importation nécessaires pour générer des applications ou des DLL qui utilisent ces DLL partagée d’extension MFC ont le même nom que la DLL, mais ont une extension de nom de fichier .lib. Lorsque vous utilisez les DLL partagées, une petite bibliothèque statique doit toujours être liée à votre code. Cette bibliothèque est nommée MFCS*version*{U} {D} .lib.

Si vous liez dynamiquement à la version DLL partagée de MFC, s’il s’agit d’une application ou d’une DLL d’extension MFC, vous devez inclure la correspondance MFC*version*. DLL ou MFC*version*U.DLL lorsque vous déployez votre produit.

Pour obtenir la liste des DLL Visual C++ qui peuvent être distribués avec vos applications, consultez [Code distribuable pour Microsoft Visual Studio 2017 et Microsoft Visual Studio 2017 SDK (inclut des utilitaires et des fichiers BuildServer)](http://go.microsoft.com/fwlink/p/?LinkId=823098).

Pour plus d’informations sur la prise en charge Unicode et MBCS dans MFC, consultez [Unicode et la prise en charge de la valeur de caractère multioctets (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Prise en charge de la bibliothèque de liens dynamiques

Vous pouvez utiliser soit statiques ou partagées dynamiques bibliothèques MFC pour créer des DLL qui peuvent être utilisées par les exécutables MFC et non-MFC. Ils sont appelés « DLL régulières » ou « DLL MFC normales », pour les distinguer des MFC DLL d’extension qui ne peut être utilisé par les applications MFC et MFC DLL. Une DLL générée en utilisant les bibliothèques statiques MFC est parfois appelée un USRDLL dans les anciennes références, car les projets de DLL MFC définissent le symbole de préprocesseur  **\_USRDLL**. Une DLL qui utilise la bibliothèque MFC des partagés DLL est parfois appelée AFXDLL dans les anciennes références, car il définit le symbole de préprocesseur  **\_AFXDLL**.

Lorsque vous créez votre projet DLL en liant les bibliothèques statiques MFC, votre DLL peut être déployée sans DLL partagées de la bibliothèque MFC. Lorsque votre projet DLL établit un lien vers les bibliothèques d’importation MFC*version*. LIB ou MFC*version*U.LIB, vous devez déployer la correspondance de MFC partagée DLL MFC*version*. DLL ou MFC*version*U.DLL avec votre DLL. Pour plus d’informations, consultez [DLL](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)  
