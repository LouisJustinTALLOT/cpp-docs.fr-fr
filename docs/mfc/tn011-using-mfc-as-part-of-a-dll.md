---
description: 'En savoir plus sur : TN011 : utilisation de MFC dans le cadre d’une DLL'
title: "TN011 : utilisation de MFC dans le cadre d'une DLL"
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 11b50ce361fc9e41c48931daa6bffd30a8c9673e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216026"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011 : utilisation de MFC dans le cadre d'une DLL

Cette note décrit les DLL MFC standard, qui vous permettent d’utiliser la bibliothèque MFC dans le cadre d’une bibliothèque de liens dynamiques (DLL) Windows. Cela suppose une certaine familiarisation avec les DLL Windows et leur mode de création. Pour plus d’informations sur les dll d’extension MFC, avec lesquelles vous pouvez créer des extensions à la bibliothèque MFC, consultez [version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>Interfaces DLL

les DLL MFC standard supposent que les interfaces entre l’application et la DLL sont spécifiées dans des fonctions de type C ou des classes exportées de manière explicite. Les interfaces de classe MFC ne peuvent pas être exportées.

Si une DLL et une application veulent utiliser MFC, elles peuvent toutes deux utiliser la version partagée des bibliothèques MFC ou utiliser un lien statiquement vers une copie des bibliothèques. L'application et la DLL peuvent toutes deux utiliser l'une des versions standard de la bibliothèque MFC.

les DLL MFC standard présentent plusieurs avantages :

- Une application qui utilise la DLL ne doit pas utiliser MFC et ne doit pas nécessairement être une application Visual C++.

- Avec les DLL MFC normales liées de manière statique aux MFC, la taille de la DLL dépend uniquement des routines MFC et C Runtime utilisées et liées.

- Avec les DLL MFC standard qui sont liées de manière dynamique aux MFC, les économies en mémoire à partir de l’utilisation de la version partagée de MFC peuvent être importantes. Toutefois, vous devez distribuer les DLL partagées, MFC \<*version*> . dll et Msvvcrt \<*version*> . dll, avec votre dll.

- La création de la DLL est indépendante de la façon dont les classes sont implémentées. La conception de DLL exporte uniquement pour les API que vous souhaitez. Par conséquent, si l’implémentation change, les DLL MFC standard sont toujours valides.

- Avec les DLL MFC normales liées de manière statique aux MFC, si la DLL et l’application utilisent les MFC, il n’y a aucun problème avec l’application qui souhaite une version différente de MFC par rapport à la DLL ou vice versa. Étant donné que la bibliothèque MFC est statiquement liée dans chaque DLL ou EXE, il n'y a aucun problème avec la version dont vous disposez.

## <a name="api-limitations"></a>Limitations API

Certaines fonctionnalités de MFC ne s'appliquent pas à la version DLL, soit en raison des limitations techniques ou parce que ces services sont généralement fournis par l'application. Avec la version actuelle de MFC, la seule fonction qui n'est pas applicable est `CWinApp::SetDialogBkColor`.

## <a name="building-your-dll"></a>Création de la DLL

Lors de la compilation de DLL MFC normales liées de manière statique aux MFC, les symboles `_USRDLL` et `_WINDLL` doivent être définis. Le code DLL doit également être compilé avec les commutateurs de compilation suivants :

- **/D_WINDLL** signifie que la compilation concerne une dll

- **/D_USRDLL** spécifie que vous générez une DLL MFC normale

Vous devez également définir ces symboles et utiliser ces commutateurs de compilateur quand vous compilez des DLL MFC normales qui sont liées de manière dynamique aux MFC. En outre, le symbole `_AFXDLL` doit être défini et le code DLL doit être compilé avec :

- **/D_AFXDLL** spécifie que vous générez une DLL MFC normale liée de manière dynamique aux MFC

Les interfaces (API) entre l'application et la DLL doivent être explicitement exportées. Nous vous recommandons de définir des interfaces à faible bande passante, et si possible, d'utiliser uniquement des interfaces C. Il est plus facile de gérer les interfaces C directes que les classes C++ plus complexes.

Placez les API dans en-tête distinct qui peut être inclus dans les fichiers C et C++. Pour obtenir un exemple, consultez l’en-tête ScreenCap. h dans MFC Advanced concepts Sample [DLLScreenCap](../overview/visual-cpp-samples.md) . Pour exporter les fonctions, écrivez-les dans la section `EXPORTS` de votre fichier de définition de module (.DEF) ou incluez `__declspec(dllexport)` dans les définitions de fonction. Utilisez `__declspec(dllimport)` pour importer ces fonctions dans le fichier exécutable client.

Vous devez ajouter la macro AFX_MANAGE_STATE au début de toutes les fonctions exportées dans des DLL MFC standard qui sont liées de manière dynamique aux MFC. La macro définit l'état du module en cours à celui de la DLL. Pour utiliser cette macro, ajoutez la ligne de code suivante au début des fonctions exportées à partir de la DLL :

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain-> DllMain

La bibliothèque MFC définit le `DllMain` point d’entrée Win32 standard qui initialise votre objet dérivé de [CWinApp](../mfc/reference/cwinapp-class.md) comme dans une application MFC classique. Placez toute l’initialisation propre à la DLL dans la méthode [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) comme dans une application MFC classique.

Notez que le mécanisme [CWinApp :: Run](../mfc/reference/cwinapp-class.md#run) ne s’applique pas à une dll, car l’application possède la pompe de messages principale. Si votre DLL affiche des boîtes de dialogue non modales ou a sa propre fenêtre frame principale, la pompe de messages principale de votre application doit appeler une routine exportée par la DLL qui appelle [CWinApp ::P retranslatemessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Pour obtenir un exemple de cette fonction, consultez l'exemple DLLScreenCap.

La `DllMain` fonction fournie par MFC appellera la méthode [CWinApp :: ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) de votre classe dérivée de `CWinApp` avant le déchargement de la dll.

## <a name="linking-your-dll"></a>Liaison de votre DLL

Avec les DLL MFC normales liées de manière statique aux MFC, vous devez lier votre DLL avec NAFXCWD. lib ou NAFXCW. lib et avec la version des runtimes C nommée LIBCMT. lib. Ces bibliothèques sont prégénérées et peuvent être installées en les spécifiant lorsque vous exécutez le programme d'installation de Visual C++.

## <a name="sample-code"></a>Exemple de code

Consultez l'exemple de programme DLLScreenCap de concepts avancés MFC pour obtenir un exemple complet. Plusieurs choses intéressantes à noter dans cet exemple :

- Les indicateurs de compilateur de la DLL et ceux de l'application sont différents.

- Les lignes de liaison et les fichiers .DEF pour la DLL et celles de l'application sont différentes.

- Une application qui utilise la DLL ne doit pas être en C++.

- L'interface entre l'application et la DLL est une API qui est utilisable par C ou C++ et est exportée avec DLLScreenCap.def.

L’exemple suivant illustre une API qui est définie dans une DLL MFC normale qui est liée de manière statique aux MFC. Dans cet exemple, la déclaration est englobée dans un bloc `extern "C" { }` pour les utilisateurs C++. Cela a plusieurs avantages. Tout d'abord, elle permet l'utilisation des API de votre DLL par des applications clientes non-C++. Ensuite, elle réduit la charge mémoire de la DLL dans la mesure où la convention des noms C++ n'est pas appliquée au nom exporté. Enfin, elle facilite l'ajout explicite de fonctions à un fichier .DEF (en vue d'une exportation ordinale) en éliminant la contrainte de la convention des noms.

```cpp
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
