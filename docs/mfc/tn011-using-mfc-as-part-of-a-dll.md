---
title: "TN011 : utilisation de MFC dans le cadre d'une DLL"
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.dll
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: e709404ed6e0ba79159131de1cbff80905e9f216
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517648"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011 : utilisation de MFC dans le cadre d'une DLL

Cette note décrit des DLL MFC normales, ce qui vous permet d’utiliser la bibliothèque MFC dans le cadre d’une bibliothèque de liens dynamiques (DLL) Windows. Cela suppose une certaine familiarisation avec les DLL Windows et leur mode de création. Pour plus d’informations sur les DLL d’extension MFC, avec lequel vous pouvez créer des extensions de la bibliothèque MFC, consultez [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>Interfaces DLL

DLL MFC normales supposent que les interfaces entre l’application et la DLL sont spécifiées dans les fonctions C ou les classes exportées explicitement. Les interfaces de classe MFC ne peuvent pas être exportées.

Si une DLL et une application veulent utiliser MFC, elles peuvent toutes deux utiliser la version partagée des bibliothèques MFC ou utiliser un lien statiquement vers une copie des bibliothèques. L'application et la DLL peuvent toutes deux utiliser l'une des versions standard de la bibliothèque MFC.

DLL MFC normales ont plusieurs avantages :

- Une application qui utilise la DLL ne doit pas utiliser MFC et ne doit pas nécessairement être une application Visual C++.

- Avec les DLL MFC standard qui lient statiquement à MFC, la taille de la DLL dépend uniquement les routines runtime C et MFC qui sont utilisées et liées.

- Avec les DLL MFC normales de manière dynamique aux MFC, les économies dans la mémoire à l’aide de la version partagée des MFC peuvent être significatifs. Toutefois, vous devez distribuer les DLL partagées, Mfc*\<version >*.dll et Msvvcrt*\<version >*.dll, avec votre DLL.

- La création de la DLL est indépendante de la façon dont les classes sont implémentées. La conception de DLL exporte uniquement pour les API que vous souhaitez. Par conséquent, si l’implémentation change, les DLL MFC normales sont toujours valides.

- Avec des DLL MFC normales liées de manière statique aux MFC, si la DLL et l’application utilisent MFC, il n’y a aucun problème avec l’application qui requiert une autre version de MFC que la DLL ou inversement. Étant donné que la bibliothèque MFC est statiquement liée dans chaque DLL ou EXE, il n'y a aucun problème avec la version dont vous disposez.

## <a name="api-limitations"></a>Limitations API

Certaines fonctionnalités de MFC ne s'appliquent pas à la version DLL, soit en raison des limitations techniques ou parce que ces services sont généralement fournis par l'application. Avec la version actuelle de MFC, la seule fonction qui n'est pas applicable est `CWinApp::SetDialogBkColor`.

## <a name="building-your-dll"></a>Création de la DLL

Lors de la compilation des DLL MFC normales liées de manière statique aux MFC, les symboles `_USRDLL` et `_WINDLL` doit être défini. Le code DLL doit également être compilé avec les commutateurs de compilation suivants :

- **/ D_WINDLL** signifie que la compilation est pour une DLL

- **/ D_USRDLL** spécifie vous générez une DLL MFC normale

Vous devez également définir ces symboles et utiliser ces commutateurs du compilateur lorsque vous compilez des DLL MFC normales liées de manière dynamique aux MFC. En outre, le symbole `_AFXDLL` doit être défini et le code DLL doit être compilé avec :

- **/ D_AFXDLL** Spécifie que vous générez une DLL MFC normale liée de manière dynamique aux MFC

Les interfaces (API) entre l'application et la DLL doivent être explicitement exportées. Nous vous recommandons de définir des interfaces à faible bande passante, et si possible, d'utiliser uniquement des interfaces C. Il est plus facile de gérer les interfaces C directes que les classes C++ plus complexes.

Placez les API dans en-tête distinct qui peut être inclus dans les fichiers C et C++. Consultez l’en-tête ScreenCap.h dans l’exemple de Concepts avancés MFC [DLLScreenCap](../visual-cpp-samples.md) pour obtenir un exemple. Pour exporter les fonctions, écrivez-les dans la section `EXPORTS` de votre fichier de définition de module (.DEF) ou incluez `__declspec(dllexport)` dans les définitions de fonction. Utilisez `__declspec(dllimport)` pour importer ces fonctions dans le fichier exécutable client.

Vous devez ajouter la macro AFX_MANAGE_STATE au début de toutes les fonctions exportées dans des DLL MFC normales liées de manière dynamique aux MFC. La macro définit l'état du module en cours à celui de la DLL. Pour utiliser cette macro, ajoutez la ligne de code suivante au début des fonctions exportées à partir de la DLL :

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

La bibliothèque MFC définit Win32 standard `DllMain` point d’entrée qui initialise votre [CWinApp](../mfc/reference/cwinapp-class.md) objet comme dans une application MFC classique dérivé. Placez l’initialisation des DLL dans le [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) méthode comme dans une application MFC classique.

Notez que le [CWinApp::Run](../mfc/reference/cwinapp-class.md#run) mécanisme ne s’applique pas à une DLL, étant donné que l’application qui possède la pompe de messages principale. Si votre DLL affiche des boîtes de dialogue non modales ou possède une fenêtre frame principale propre, pompe de messages principale de votre application doit appeler une routine exportée par la DLL qui appelle [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Pour obtenir un exemple de cette fonction, consultez l'exemple DLLScreenCap.

Le `DllMain` fonction MFC fournit appelle la [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) méthode de votre classe dérivée de `CWinApp` avant de la DLL est déchargée.

## <a name="linking-your-dll"></a>Liaison de votre DLL

Avec les DLL MFC standard qui lient statiquement à MFC, vous devez lier votre DLL à Nafxcwd.lib ou Nafxcw.lib et avec la version des runtimes C nommés Libcmt.lib. Ces bibliothèques sont prégénérées et peuvent être installées en les spécifiant lorsque vous exécutez le programme d'installation de Visual C++.

## <a name="sample-code"></a>Exemple de code

Consultez l'exemple de programme DLLScreenCap de concepts avancés MFC pour obtenir un exemple complet. Plusieurs choses intéressantes à noter dans cet exemple :

- Les indicateurs de compilateur de la DLL et ceux de l'application sont différents.

- Les lignes de liaison et les fichiers .DEF pour la DLL et celles de l'application sont différentes.

- Une application qui utilise la DLL ne doit pas être en C++.

- L'interface entre l'application et la DLL est une API qui est utilisable par C ou C++ et est exportée avec DLLScreenCap.def.

L’exemple suivant illustre une API qui est définie dans une DLL MFC qui lie statiquement à MFC standard. Dans cet exemple, la déclaration est englobée dans un bloc `extern "C" { }` pour les utilisateurs C++. Cela a plusieurs avantages. Tout d'abord, elle permet l'utilisation des API de votre DLL par des applications clientes non-C++. Ensuite, elle réduit la charge mémoire de la DLL dans la mesure où la convention des noms C++ n'est pas appliquée au nom exporté. Enfin, elle facilite l'ajout explicite de fonctions à un fichier .DEF (en vue d'une exportation ordinale) en éliminant la contrainte de la convention des noms.

```
#ifdef __cplusplus
extern "C" {
#endif  /* __cplusplus */

struct TracerData
{
    BOOL bEnabled;
    UINT flags;
};

BOOL PromptTraceFlags(TracerData FAR* lpData);

#ifdef __cplusplus
}
#endif
```

Les structures utilisées par l'API ne sont pas dérivées des classes de MFC et sont définies dans l'en-tête d'API. Il est ainsi possible de réduire la complexité de l'interface entre la DLL et l'application et rend la DLL utilisable pour les programmes C.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

