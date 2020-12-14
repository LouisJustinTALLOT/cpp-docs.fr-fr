---
description: En savoir plus sur les versions de bibliothèque MFC
title: Versions de bibliothèque MFC
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: 26d17604ec201deffd5fd2d5e843269e67e3dd07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280584"
---
# <a name="mfc-library-versions"></a>Versions de bibliothèque MFC

La bibliothèque MFC est disponible dans les versions qui prennent en charge le code MBCS codé sur un octet et sur un jeu de caractères multioctets (MBCS), ainsi que les versions qui prennent en charge Unicode (codé au format UTF-16LE, jeu de caractères natif de Windows). Chaque version de MFC est disponible en tant que bibliothèque statique ou en tant que DLL partagée. Il existe également une plus petite version de bibliothèque statique MFC qui laisse les contrôles MFC pour les boîtes de dialogue, pour les applications qui sont très sensibles à la taille et qui n’ont pas besoin de ces contrôles. Les bibliothèques MFC sont disponibles à la fois dans les versions Debug et Release pour les architectures prises en charge qui incluent des processeurs x86, x64 et ARM. Vous pouvez créer des applications (fichiers. exe) et des dll avec n’importe quelle version des bibliothèques MFC. Il existe également un ensemble de bibliothèques MFC compilées pour l’interfaçage avec du code managé. Les DLL partagées MFC incluent un numéro de version pour indiquer la compatibilité binaire de la bibliothèque.

## <a name="automatic-linking-of-mfc-library-versions"></a>Liaison automatique des versions de la bibliothèque MFC

Les fichiers d’en-tête MFC déterminent automatiquement la version appropriée de la bibliothèque MFC à lier, en fonction des valeurs définies dans votre environnement de génération. Les fichiers d’en-tête MFC ajoutent des directives de compilateur qui demandent à l’éditeur de liens de créer un lien dans une version spécifique de la bibliothèque MFC.

Par exemple, AFX. Le fichier d’en-tête H demande à l’éditeur de liens de se lier à la version DLL complète statique, limitée ou partagée de MFC ; Version ANSI/MBCS ou Unicode ; et débogage ou version commerciale, en fonction de votre configuration de build :

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

Les fichiers d’en-tête MFC incluent également des directives à lier dans toutes les bibliothèques requises, notamment les bibliothèques MFC, les bibliothèques Win32, les bibliothèques OLE, les bibliothèques OLE créées à partir d’exemples, les bibliothèques ODBC, etc.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS et Unicode

Les versions de bibliothèque MFC ANSI/MBCS prennent en charge les jeux de caractères codés sur un octet tels que ASCII et les jeux de caractères multioctets tels que Shift-JIS. Les versions de bibliothèque Unicode MFC prennent en charge Unicode dans sa forme encodée en caractères larges UTF-16LE. Utilisez les versions de bibliothèque ANSI/MBCS de MFC pour la prise en charge Unicode encodée en UTF-8.

Pour définir la configuration de votre projet de façon à utiliser la prise en charge des caractères et des chaînes Unicode sur un octet, multioctets ou à caractères larges dans l’IDE, utilisez la boîte de dialogue **Propriétés du projet** . Dans la page **Propriétés de configuration**  >  **général** , définissez la propriété **jeu de caractères** sur **non défini** sur utiliser un jeu de caractères codés sur un octet. Affectez à la propriété la **valeur utiliser le jeu de caractères** multioctets pour utiliser un jeu de caractères multioctets, ou pour utiliser le **jeu de caractères Unicode** pour utiliser le codage Unicode UTF-16.

Les projets MFC utilisent le symbole de préprocesseur \_ Unicode pour indiquer la prise en charge Unicode UTF-16 à caractères larges, et \_ MBCS pour indiquer la prise en charge MBCS. Ces options s’excluent mutuellement dans un projet.

## <a name="mfc-static-library-naming-conventions"></a>Conventions de nommage des bibliothèques statiques MFC

Les bibliothèques statiques pour MFC utilisent les conventions d’affectation de noms suivantes. Les noms de bibliothèque se présentent sous la forme

> <em>u</em> <em>CD</em>AFX. LIB

où les lettres en minuscules en italique sont des espaces réservés pour les spécificateurs dont les significations sont indiquées dans le tableau suivant :

|Spécificateur|Valeurs et significations|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) ou Unicode (U); omettre pour la version sans contrôles MFC dans les boîtes de dialogue|
|*c*|Version avec des contrôles MFC dans les boîtes de dialogue (CW) ou sans (NMCD)|
|*d*|Debug ou Release : D = debug ; spécificateur d’omission pour la mise en sortie|

Toutes les bibliothèques répertoriées dans le tableau suivant sont incluses prégénérées dans le répertoire \atlmfc\lib pour les architectures de build prises en charge.

|Bibliothèque|Description|
|-------------|-----------------|
|NAFXCW.LIB|Bibliothèque de Static-Link MFC, version Release|
|NAFXCWD.LIB|Bibliothèque de Static-Link MFC, version de débogage|
|UAFXCW. LIB|Bibliothèque de Static-Link MFC avec prise en charge Unicode, version Release|
|UAFXCWD. LIB|Bibliothèque de Static-Link MFC avec prise en charge Unicode, version de débogage|
|AFXNMCD. LIB|Bibliothèque de Static-Link MFC sans contrôles de boîte de dialogue MFC, version Release|
|AFXNMCDD. LIB|Bibliothèque de Static-Link MFC sans contrôles de boîte de dialogue MFC, version de débogage|

Les fichiers du débogueur qui ont le même nom de base et une extension. pdb sont également disponibles pour chacune des bibliothèques statiques.

## <a name="mfc-shared-dll-naming-conventions"></a>Conventions de nommage des DLL partagées MFC

Les DLL partagées MFC suivent également une convention d’affectation de noms structurée. Cela facilite la connaissance de la DLL ou de la bibliothèque à utiliser à cet effet.

Les DLL MFC ont des numéros de *version* qui indiquent la compatibilité binaire. Utilisez des DLL MFC dont la version est identique à celle des autres bibliothèques et de l’ensemble d’outils du compilateur pour garantir la compatibilité au sein d’un projet.

|DLL|Description|
|---------|-----------------|
|*Version* MFC. DLL|DLL MFC, version ANSI ou MBCS|
|*Version* MFCU.DLL|DLL MFC, version de la version Unicode|
|*Version* MFCD.DLL|DLL MFC, version de débogage ANSI ou MBCS|
|*Version* MFCUD.DLL|DLL MFC, version de débogage Unicode|
|*Version* de MFCM. DLL|DLL MFC avec les contrôles Windows Forms, version ANSI ou MBCS|
|*Version* de MFCMU.DLL|DLL MFC avec contrôles de Windows Forms, version de version Unicode|
|*Version* de MFCMD.DLL|DLL MFC avec contrôles de Windows Forms, version de débogage ANSI ou MBCS|
|*Version* de MFCMUD.DLL|DLL MFC avec contrôles de Windows Forms, version de débogage Unicode|

Les bibliothèques d’importation nécessaires pour générer des applications ou des dll d’extension MFC qui utilisent ces DLL partagées ont le même nom de base que la DLL, mais ont une extension de nom de fichier. lib. Lorsque vous utilisez les DLL partagées, une petite bibliothèque statique doit toujours être liée à votre code ; Cette bibliothèque est nommée MFCS *version*{U} {D}. lib.

Si vous effectuez une liaison dynamique à la version DLL partagée de MFC, qu’il s’agisse d’une application ou d’une DLL d’extension MFC, vous devez inclure la *version* MFC correspondante. DLL ou *version* MFCU.DLL lorsque vous déployez votre produit.

Pour obtenir la liste des DLL Visual C++ qui peuvent être distribuées avec vos applications, consultez le [code distribuable pour Microsoft Visual Studio 2017 et Microsoft Visual Studio 2017 SDK (y compris les utilitaires et les fichiers BuildServer)](/visualstudio/productinfo/2017-redistribution-vs) ou le [code distribuable pour Visual Studio 2019](/visualstudio/releases/2019/redistribution).

Pour plus d’informations sur la prise en charge MBCS et Unicode dans MFC, consultez [prise en charge des jeux de caractères Unicode et MBCS](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Prise en charge des bibliothèques de liens dynamiques

Vous pouvez utiliser les bibliothèques MFC dynamiques statiques ou partagées pour créer des dll qui peuvent être utilisées par les exécutables MFC et non-MFC. Celles-ci sont appelées « DLL normales » ou « DLL MFC standard » pour les distinguer des dll d’extension MFC qui peuvent uniquement être utilisées par les applications MFC et les DLL MFC. Une DLL générée à l’aide des bibliothèques statiques MFC est parfois appelée USRDLL dans des références plus anciennes, car les projets DLL MFC définissent le symbole de préprocesseur **\_ USRDLL**. Une DLL qui utilise les DLL partagées MFC est parfois appelée AFXDLL dans des références plus anciennes, car elle définit le symbole de préprocesseur **\_ AFXDLL**.

Lorsque vous créez votre projet DLL en établissant une liaison avec les bibliothèques statiques MFC, votre DLL peut être déployée sans les DLL partagées MFC. Lorsque votre projet DLL est lié à la *version* MFC des bibliothèques d’importation. LIB ou MFC *version* U. lib, vous devez déployer la *version* MFC partagée DLL MFC correspondante. DLL ou *version* MFCU.DLL avec votre dll. Pour plus d’informations, consultez [dll](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Rubriques générales sur MFC](general-mfc-topics.md)
