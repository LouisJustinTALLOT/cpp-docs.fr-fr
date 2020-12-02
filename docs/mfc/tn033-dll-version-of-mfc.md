---
title: 'TN033 : version DLL de MFC'
description: Montre comment utiliser les bibliothèques de liens dynamiques partagées MFC avec les applications MFC et les dll d’extension MFC.
ms.date: 11/30/2020
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.openlocfilehash: b9330fe7c756f962a8b06a04b840bfda343f3a49
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440313"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033 : version DLL de MFC

Cette note décrit comment vous pouvez utiliser les *`MFCxx.DLL`* *`MFCxxD.DLL`* bibliothèques de liens dynamiques partagées et (où *XX* est le numéro de version MFC) avec les applications MFC et les dll d’extension MFC. Pour plus d’informations sur les DLL MFC standard, consultez [utilisation de MFC dans le cadre d’une dll](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Cette note technique couvre trois aspects des dll. Les deux derniers sont destinés aux utilisateurs les plus avancés :

- [Comment créer une DLL d’extension MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Comment créer une application MFC qui utilise la version DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Comment les bibliothèques de liens dynamiques partagées MFC sont implémentées](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Si vous souhaitez créer une DLL à l’aide de MFC qui peut être utilisée avec des applications non-MFC (appelées *DLL MFC standard*), reportez-vous à la [note technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Vue d’ensemble de la prise en charge de MFCxx.DLL : terminologie et fichiers

**DLL MFC normale**: vous utilisez une DLL MFC normale pour générer une dll autonome à l’aide de certaines des classes MFC. Les interfaces sur les limites de l’application/DLL sont des interfaces « C », et l’application cliente ne doit pas nécessairement être une application MFC.

Les DLL MFC standard sont la version des dll prises en charge dans MFC 1,0. Elles sont décrites dans [Technical Note 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) et l’exemple MFC Advanced concepts [`DLLScreenCap`](../overview/visual-cpp-samples.md) .

> [!NOTE]
> À partir de Visual C++ version 4,0, le terme **USRDLL** est obsolète et a été remplacé par une DLL MFC normale qui est liée de manière statique aux MFC. Vous pouvez également générer une DLL MFC normale qui est liée de manière dynamique aux MFC.

MFC 3,0 (et versions ultérieures) prend en charge les DLL MFC classiques avec toutes les nouvelles fonctionnalités, notamment les classes OLE et de base de données.

**AFXDLL**: également appelée version partagée des bibliothèques MFC. Il s’agit de la nouvelle prise en charge des DLL ajoutée dans MFC 2,0. La bibliothèque MFC elle-même se trouve dans un certain nombre de dll (décrites ci-dessous). Une application cliente ou une DLL lie dynamiquement les dll dont elle A besoin. Les interfaces entre les limites d’application/DLL sont des interfaces de classe C++/MFC. L’application cliente doit être une application MFC. Cette DLL prend en charge toutes les fonctionnalités MFC 3,0 (exception : UNICODE n’est pas pris en charge pour les classes de base de données).

> [!NOTE]
> À partir de Visual C++ version 4,0, ce type de DLL est appelé « DLL d’extension ».

Cette remarque utilisera *`MFCxx.DLL`* pour faire référence à l’ensemble de la DLL MFC, qui comprend :

- Débogage : *`MFCxxD.DLL`* (combiné) et *`MFCSxxD.LIB`* (statique).

- Version : *`MFCxx.DLL`* (combiné) et *`MFCSxx.LIB`* (statique).

- Débogage Unicode : *`MFCxxUD.DLL`* (combiné) et *`MFCSxxD.LIB`* (statique).

- Version Unicode : *`MFCxxU.DLL`* (combiné) et *`MFCSxxU.LIB`* (statique).

> [!NOTE]
> Les *`MFCSxx[U][D].LIB`* bibliothèques sont utilisées conjointement avec les DLL partagées MFC. Ces bibliothèques contiennent du code qui doit être lié de manière statique à l’application ou à la DLL.

Une application est liée aux bibliothèques d’importation correspondantes :

- Debug *`MFCxxD.LIB`*

- 3/05 *`MFCxx.LIB`*

- Débogage Unicode : *`MFCxxUD.LIB`*

- Version Unicode : *`MFCxxU.LIB`*

Une *dll d’extension MFC* est une dll qui étend *`MFCxx.DLL`* (ou les autres DLL partagées MFC). Ici, l’architecture des composants MFC démarre. Si vous dérivez une classe utile d’une classe MFC ou si vous créez une autre boîte à outils de type MFC, vous pouvez la placer dans une DLL. Votre DLL utilise *`MFCxx.DLL`* , tout comme l’application cliente finale. Une DLL d’extension MFC autorise les classes de feuille réutilisables, les classes de base réutilisables et les classes d’affichage et de document réutilisables.

## <a name="pros-and-cons"></a>Avantages et inconvénients

Pourquoi utiliser la version partagée de MFC ?

- L’utilisation de la bibliothèque partagée peut entraîner des applications plus petites. (Une application minimale qui utilise la plupart de la bibliothèque MFC est inférieure à 10 Ko).

- La version partagée de MFC prend en charge les dll d’extension MFC et les DLL MFC standard.

- Il est plus rapide de créer une application qui utilise les bibliothèques MFC partagées qu’une application MFC liée de manière statique. Cela est dû au fait qu’il n’est pas nécessaire de lier MFC lui-même. C’est particulièrement vrai dans **`DEBUG`** les builds où l’éditeur de liens doit compacter les informations de débogage. Lorsque votre application est liée à une DLL qui contient déjà les informations de débogage, il y a moins d’informations de débogage à compacter.

Pourquoi ne pas utiliser la version partagée de MFC :

- L’expédition d’une application qui utilise la bibliothèque partagée nécessite que vous fournissez *`MFCxx.DLL`* et d’autres bibliothèques avec votre programme. *`MFCxx.DLL`* est redistribuable librement comme de nombreuses dll, mais vous devez toujours installer la DLL dans votre programme d’installation. En outre, vous devrez livrer les autres bibliothèques redistribuables utilisées à la fois par votre programme et les DLL MFC elles-mêmes.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Comment écrire une DLL d’extension MFC

Une DLL d’extension MFC est une DLL qui contient des classes et des fonctions pour étendre les fonctionnalités des classes MFC. Une DLL d’extension MFC utilise les DLL MFC partagées de la même façon qu’une application les utilise, avec quelques considérations supplémentaires :

- Le processus de génération est semblable à la création d’une application qui utilise les bibliothèques MFC partagées avec quelques options supplémentaires du compilateur et de l’éditeur de liens.

- Une DLL d’extension MFC n’a pas de `CWinApp` classe dérivée de.

- Une DLL d’extension MFC doit fournir un spécial `DllMain` . AppWizard fournit une `DllMain` fonction que vous pouvez modifier.

- Une DLL d’extension MFC fournit normalement une routine d’initialisation pour créer un `CDynLinkLibrary` , si la dll d’extension MFC exporte des `CRuntimeClass` types ou des ressources vers l’application. Une classe dérivée de `CDynLinkLibrary` peut être utilisée si les données par application doivent être gérées par la dll d’extension MFC.

Ces considérations sont décrites plus en détail ci-dessous. Reportez-vous également à l’exemple MFC Advanced concepts [`DLLHUSK`](../overview/visual-cpp-samples.md) . Il montre comment :

- Générez une application à l’aide des bibliothèques partagées. ( *`DLLHUSK.EXE`* est une application MFC qui est liée de manière dynamique aux bibliothèques MFC et à d’autres dll.)

- Générez une DLL d’extension MFC. (Il montre comment des indicateurs spéciaux, tels que, `_AFXEXT` sont utilisés lors de la génération d’une DLL d’extension MFC.)

- Générez deux exemples de DLL d’extension MFC. L’une d’elles illustre la structure de base d’une DLL d’extension MFC avec des exportations limitées (TESTDLL1) et l’autre montre l’exportation d’une interface de classe entière (TESTDLL2).

L’application cliente et toutes les dll d’extension MFC doivent utiliser la même version de *`MFCxx.DLL`* . Suivez les conventions des DLL MFC et fournissez une version Debug et Release ( **`/release`** ) de votre dll d’extension MFC. Cette pratique permet aux programmes clients de générer des versions Debug et Release de leurs applications et de les lier à la version Debug ou Release appropriée de toutes les dll.

> [!NOTE]
> Étant donné que les problèmes de gestion et d’exportation des noms C++, la liste d’exportation à partir d’une DLL d’extension MFC peut être différente entre les versions Debug et Release de la même DLL et des dll pour différentes plateformes. La version *`MFCxx.DLL`* comporte environ 2000 points d’entrée exportés ; le débogage *`MFCxxD.DLL`* a environ 3000 points d’entrée exportés.

### <a name="quick-note-on-memory-management"></a>Note rapide sur la gestion de la mémoire

La section intitulée « gestion de la mémoire », vers la fin de cette note technique, décrit l’implémentation de *`MFCxx.DLL`* avec la version partagée de MFC. Les informations que vous devez connaître pour implémenter uniquement une DLL d’extension MFC sont décrites ici.

*`MFCxx.DLL`* et toutes les dll d’extension MFC chargées dans l’espace d’adressage d’une application cliente utiliseront la même allocation de mémoire, le chargement des ressources et d’autres États « globaux » MFC comme s’ils se trouvaient dans la même application. C’est important, car les bibliothèques DLL non-MFC et les DLL MFC régulières liées de manière statique aux MFC font exactement le contraire : chaque DLL alloue de son propre pool de mémoire.

Si une DLL d’extension MFC alloue de la mémoire, cette mémoire peut être mélangée librement avec tout autre objet alloué par l’application. En outre, si une application qui utilise les bibliothèques MFC partagées se bloque, le système d’exploitation maintient l’intégrité de toute autre application MFC qui partage la DLL.

De même, d’autres États MFC « globaux » tels que le fichier exécutable actuel pour charger des ressources, sont également partagés entre l’application cliente, toutes les dll d’extension MFC et *`MFCxx.DLL`* elle-même.

### <a name="building-an-mfc-extension-dll"></a>Génération d’une DLL d’extension MFC

Vous pouvez utiliser AppWizard pour créer un projet de DLL d’extension MFC et génère automatiquement les paramètres de compilateur et de l’éditeur de liens appropriés. Elle génère également une `DllMain` fonction que vous pouvez modifier.

Si vous convertissez un projet existant en DLL d’extension MFC, commencez par les paramètres standard qui sont générés à l’aide de la version partagée de MFC. Apportez ensuite les modifications suivantes :

- Ajoutez **`/D_AFXEXT`** aux indicateurs du compilateur. Dans la boîte de dialogue Propriétés du projet, sélectionnez la catégorie de préprocesseur **C/C++**  >  **Preprocessor** . Ajoutez `_AFXEXT` au champ **définir des macros** , en séparant chacun des éléments par des points-virgules.

- Supprimez le **`/Gy`** commutateur du compilateur. Dans la boîte de dialogue Propriétés du projet, sélectionnez la catégorie génération de code **C/C++**  >  **Code Generation** . Assurez-vous que la propriété **activer la liaison de Function-Level** n’est pas activée. Ce paramètre facilite l’exportation des classes, car l’éditeur de liens ne supprime pas les fonctions non référencées. Si le projet d’origine a généré une DLL MFC normale liée de manière statique aux MFC, remplacez l' **`/MT`** option de compilateur (ou **`/MTd`** ) par **`/MD`** (ou **`/MDd`** ).

- Générez une bibliothèque d’exportation avec l' **`/DLL`** option de liaison. Cette option est définie lorsque vous créez une cible et que vous spécifiez la bibliothèque de Dynamic-Link Win32 comme type de cible.

### <a name="changing-your-header-files"></a>Modification de vos fichiers d’en-tête

L’objectif habituel d’une DLL d’extension MFC est d’exporter des fonctionnalités communes vers une ou plusieurs applications qui peuvent utiliser cette fonctionnalité. Fondamentalement, la DLL exporte des classes et des fonctions globales pour une utilisation par vos applications clientes.

Pour vous assurer que chaque fonction membre est marquée pour l’importation ou l’exportation selon le cas, utilisez les déclarations spéciales `__declspec(dllexport)` et `__declspec(dllimport)` . Lorsque les applications clientes utilisent vos classes, vous souhaitez qu’elles soient déclarées comme `__declspec(dllimport)` . Lorsque la DLL d’extension MFC est générée, les fonctions doivent être déclarées comme `__declspec(dllexport)` . La DLL générée doit également exporter les fonctions, afin que les programmes clients puissent s’y lier au moment du chargement.

Pour exporter votre classe entière, utilisez `AFX_EXT_CLASS` dans la définition de classe. L’infrastructure définit cette macro comme `__declspec(dllexport)` lorsque `_AFXDLL` et `_AFXEXT` est défini, mais le définit comme `__declspec(dllimport)` quand `_AFXEXT` n’est pas défini. `_AFXEXT` est défini uniquement lors de la génération de votre DLL d’extension MFC. Par exemple :

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Non-exportation de la classe entière

Il peut arriver que vous souhaitiez exporter uniquement les membres nécessaires individuels de votre classe. Par exemple, si vous exportez une `CDialog` classe dérivée de, vous devrez peut-être exporter le constructeur et l' `DoModal` appel. Vous pouvez exporter ces membres à l’aide du fichier DEF de la DLL, mais vous pouvez également utiliser à `AFX_EXT_CLASS` peu près de la même façon sur les membres individuels que vous devez exporter.

Par exemple :

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

Dans ce cas, vous risquez de rencontrer un problème supplémentaire, car vous n’exportez pas tous les membres de la classe. Le problème est lié à la façon dont les macros MFC fonctionnent. Plusieurs macros d’assistance MFC déclarent ou définissent en fait des membres de données. Votre DLL doit également exporter ces membres de données.

Par exemple, la macro DECLARE_DYNAMIC est définie comme suit lors de la génération d’une DLL d’extension MFC :

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

La ligne qui commence `static AFX_DATA` déclare un objet statique à l’intérieur de votre classe. Pour exporter cette classe correctement et accéder aux informations d’exécution à partir d’un EXE client, vous devez exporter cet objet statique. Étant donné que l’objet statique est déclaré avec le modificateur `AFX_DATA` , il vous suffit de définir `AFX_DATA` comme `__declspec(dllexport)` lorsque vous générez votre dll. Définissez-le comme `__declspec(dllimport)` lorsque vous générez votre exécutable client.

Comme indiqué ci-dessus, `AFX_EXT_CLASS` est déjà défini de cette façon. Il vous suffit de redéfinir `AFX_DATA` pour être le même que dans la `AFX_EXT_CLASS` définition de votre classe.

Par exemple :

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS
class CExampleView : public CView
{
    DECLARE_DYNAMIC()
    // ... class definition ...
};
#undef  AFX_DATA
#define AFX_DATA
```

Comme MFC utilise toujours le `AFX_DATA` symbole sur les éléments de données qu’il définit dans ses macros, cette technique fonctionnera pour tous les scénarios de ce type. Par exemple, il fonctionne pour DECLARE_MESSAGE_MAP.

> [!NOTE]
> Si vous exportez la classe entière plutôt que les membres sélectionnés de la classe, les données membres statiques sont exportées automatiquement.

Vous pouvez utiliser la même technique pour exporter automatiquement l' `CArchive` opérateur d’extraction pour les classes qui utilisent les macros DECLARE_SERIAL et IMPLEMENT_SERIAL. Exportez l’opérateur d’archive en délimitant les déclarations de classe (situées dans le fichier d’en-tête) avec le code suivant :

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Limitations de _AFXEXT

Vous pouvez utiliser le `_AFXEXT` symbole de préprocesseur pour vos dll d’extension MFC tant que vous n’avez pas plusieurs couches de DLL d’extension MFC. Si vous avez des dll d’extension MFC qui appellent ou dérivent de classes dans vos propres DLL d’extension MFC, qui dérivent ensuite des classes MFC, vous devez utiliser votre propre symbole de préprocesseur pour éviter toute ambiguïté.

Le problème est que dans Win32, vous devez déclarer explicitement toutes les données comme `__declspec(dllexport)` pour les exporter à partir d’une dll et les `__declspec(dllimport)` Importer à partir d’une dll. Lorsque vous définissez `_AFXEXT` , les en-têtes MFC s’assurent que `AFX_EXT_CLASS` est défini correctement.

Lorsque vous avez plusieurs couches, un symbole tel que `AFX_EXT_CLASS` n’est pas suffisant : une DLL d’extension MFC peut exporter ses propres classes et également importer d’autres classes à partir d’une autre DLL d’extension MFC. Pour résoudre ce problème, utilisez un symbole de préprocesseur spécial qui indique que vous générez la DLL elle-même, au lieu d’utiliser la DLL. Par exemple, Imaginez deux DLL d’extension MFC, *`A.DLL`* et *`B.DLL`* . Elles exportent chacune certaines classes dans *`A.H`* et *`B.H`* , respectivement. *`B.DLL`* utilise les classes de *`A.DLL`* . Les fichiers d’en-tête ressemblent à ceci :

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

Lorsque *`A.DLL`* est construit, il est généré avec **`/DA_IMPL`** et lorsque *`B.DLL`* est généré, il est généré avec **`/DB_IMPL`** . En utilisant des symboles distincts pour chaque DLL, `CExampleB` est exporté et `CExampleA` est importé lors de la génération *`B.DLL`* . `CExampleA` est exporté lors de la génération *`A.DLL`* et de l’importation lorsqu’il est utilisé par *`B.DLL`* ou un autre client.

Ce type de superposition ne peut pas être effectué lors de l’utilisation `AFX_EXT_CLASS` des `_AFXEXT` symboles de préprocesseur intégrés et. La technique décrite ci-dessus résout ce problème de la même façon que MFC. MFC utilise cette technique lors de la création de ses dll d’extension OLE, de base de données et de réseau.

### <a name="not-exporting-the-entire-class"></a>Non-exportation de la classe entière

Là encore, vous devez faire particulièrement attention lorsque vous n’exportez pas une classe entière. Assurez-vous que les éléments de données nécessaires créés par les macros MFC sont exportés correctement. Vous pouvez le faire en redéfinissant `AFX_DATA` la macro de votre classe spécifique. Redéfinissez-le chaque fois que vous n’exportez pas la classe entière.

Par exemple :

```cpp
// A.H
#ifdef A_IMPL
    #define CLASS_DECL_A  _declspec(dllexport)
#else
    #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
    DECLARE_DYNAMIC()
    CLASS_DECL_A int SomeFunction();
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

Voici le code que vous devez placer dans votre fichier source principal pour votre DLL d’extension MFC. Il doit venir après les inclusions standard. Quand vous utilisez AppWizard pour créer des fichiers de démarrage pour une DLL d’extension MFC, il fournit un `DllMain` pour vous.

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

L’appel à `AfxInitExtensionModule` capture les classes Runtime (structures) du module `CRuntimeClass` et ses fabriques d’objets ( `COleObjectFactory` objets) pour une utilisation ultérieure lors de la création de l' `CDynLinkLibrary` objet. L’appel de (facultatif) `AfxTermExtensionModule` permet à MFC de nettoyer la dll d’extension MFC lorsque chaque processus se détache (ce qui se produit lorsque le processus se termine, ou lorsque la dll est déchargée par un `FreeLibrary` appel) de la dll d’extension MFC. Étant donné que la plupart des dll d’extension MFC ne sont pas chargées dynamiquement (normalement, elles sont liées via leurs bibliothèques d’importation), l’appel à `AfxTermExtensionModule` n’est généralement pas nécessaire.

Si votre application charge et libère des dll d’extension MFC de manière dynamique, veillez à appeler `AfxTermExtensionModule` comme indiqué ci-dessus. Veillez également à utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions `LoadLibrary` Win32 `FreeLibrary` et) si votre application utilise plusieurs threads ou si elle charge dynamiquement une DLL d’extension MFC. L’utilisation `AfxLoadLibrary` de et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la dll d’extension MFC est chargée et déchargée n’endommage pas l’état global des MFC.

Le fichier d’en-tête *`AFXDLLX.H`* contient des définitions spéciales pour les structures utilisées dans les dll d’extension MFC, telles que la définition pour `AFX_EXTENSION_MODULE` et `CDynLinkLibrary` .

Le *extensionDLL* global doit être déclaré comme indiqué. Contrairement à la version 16 bits de MFC, vous pouvez allouer de la mémoire et appeler des fonctions MFC pendant ce temps, car le *`MFCxx.DLL`* est entièrement initialisé au moment où votre `DllMain` est appelé.

### <a name="sharing-resources-and-classes"></a>Partage des ressources et des classes

Les dll d’extension MFC simples doivent uniquement exporter quelques fonctions à faible bande passante vers l’application cliente, et rien de plus. D’autres dll gourmandes en interface utilisateur peuvent souhaiter exporter des ressources et des classes C++ vers l’application cliente.

L’exportation des ressources s’effectue par le biais d’une liste de ressources. Dans chaque application correspond une liste d’objets liée de façon unique `CDynLinkLibrary` . Lors de la recherche d’une ressource, la plupart des implémentations MFC standard qui chargent les ressources s’affichent d’abord dans le module de ressource en cours ( `AfxGetResourceHandle` ) et, si elles ne sont pas trouvées, parcourent la liste des `CDynLinkLibrary` objets tentant de charger la ressource demandée.

La création dynamique d’objets C++ en fonction d’un nom de classe C++ est similaire. Le mécanisme de désérialisation des objets MFC doit avoir tous les objets inscrits pour pouvoir être `CRuntimeClass` reconstruit en créant de manière dynamique l’objet C++ du type requis en fonction de ce qui a été stocké précédemment.

Si vous souhaitez que l’application cliente utilise des classes de votre DLL d’extension MFC qui sont `DECLARE_SERIAL` , vous devez exporter vos classes pour les rendre visibles à l’application cliente. Elle est également effectuée en parcourant la `CDynLinkLibrary` liste.

Dans l’exemple MFC Advanced concepts [`DLLHUSK`](../overview/visual-cpp-samples.md) , la liste ressemble à ceci :

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

L' *`MFCxx.DLL`* entrée vient généralement en dernier dans la liste des ressources et des classes. *`MFCxx.DLL`* inclut toutes les ressources MFC standard, y compris les chaînes de demande pour tous les ID de commande standard. Le fait de le placer à la fin de la liste permet aux dll et à l’application cliente de s’appuyer sur les ressources partagées dans le *`MFCxx.DLL`* , au lieu d’avoir leurs propres copies.

La fusion des ressources et des noms de classes de toutes les dll dans l’espace de noms de l’application cliente présente l’inconvénient que vous devez faire attention aux ID ou noms que vous choisissez. Vous pouvez désactiver cette fonctionnalité en n’exportant ni vos ressources, ni un `CDynLinkLibrary` objet vers l’application cliente. L' [`DLLHUSK`](../overview/visual-cpp-samples.md) exemple gère l’espace de noms de ressources partagées à l’aide de plusieurs fichiers d’en-tête. Pour plus d’informations sur l’utilisation des fichiers de ressources partagées, consultez la [note technique 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) .

### <a name="initializing-the-dll"></a>Initialisation de la DLL

Comme indiqué ci-dessus, vous souhaiterez généralement créer un `CDynLinkLibrary` objet pour exporter vos ressources et classes vers l’application cliente. Vous devez fournir un point d’entrée exporté pour initialiser la DLL. Au minimum, il s’agit d’une `void` routine qui n’accepte aucun argument et ne retourne rien, mais il peut s’agir de tout ce que vous aimez.

Chaque application cliente qui souhaite utiliser votre DLL doit appeler cette routine d’initialisation, si vous utilisez cette approche. Vous pouvez également allouer cet `CDynLinkLibrary` objet dans votre `DllMain` juste après avoir appelé `AfxInitExtensionModule` .

La routine d’initialisation doit créer un `CDynLinkLibrary` objet dans le tas de l’application actuelle, connecté à vos informations de DLL d’extension MFC. Vous pouvez le faire en définissant une fonction similaire à celle-ci :

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Le nom de la routine, *InitXxxDLL* dans cet exemple, peut être tout ce que vous souhaitez. Elle n’a pas besoin d’être **`extern "C"`** , mais elle facilite la gestion de la liste d’exportation.

> [!NOTE]
> Si vous utilisez votre DLL d’extension MFC à partir d’une DLL MFC normale, vous devez exporter cette fonction d’initialisation. Cette fonction doit être appelée à partir de la DLL MFC normale avant d’utiliser des classes ou des ressources DLL d’extension MFC.

### <a name="exporting-entries"></a>Exportation d’entrées

Le moyen le plus simple d’exporter vos classes consiste à utiliser `__declspec(dllimport)` et `__declspec(dllexport)` sur chaque classe et fonction globale que vous souhaitez exporter. C’est beaucoup plus facile, mais il est moins efficace que de nommer chaque point d’entrée dans un fichier DEF comme décrit ci-dessous. Cela est dû au fait que vous avez moins de contrôle sur les fonctions qui sont exportées. Et, vous ne pouvez pas exporter les fonctions par ordinal. TESTDLL1 et TESTDLL2 utilisent cette méthode pour exporter leurs entrées.

Une méthode plus efficace consiste à exporter chaque entrée en la nommant dans le fichier DEF. Cette méthode est utilisée par *`MFCxx.DLL`* . Étant donné que nous exportons de manière sélective à partir de notre DLL, nous devons décider quelles interfaces particulières nous souhaitons exporter. C’est difficile, car vous devez spécifier les noms tronqués à l’éditeur de liens sous la forme d’entrées dans le fichier DEF. N’exportez aucune classe C++, sauf si vous avez vraiment besoin d’un lien symbolique pour celle-ci.

Si vous avez essayé d’exporter des classes C++ avec un fichier DEF avant, vous souhaiterez peut-être développer un outil pour générer automatiquement cette liste. Vous pouvez le faire à l’aide d’un processus de liaison en deux étapes. Liez votre DLL une seule fois sans exportation et autorisez l’éditeur de liens à générer un fichier de mappage. Le fichier de mappage contient une liste des fonctions qui doivent être exportées. Une fois la réorganisation, vous pouvez l’utiliser pour générer les entrées d’exportation pour votre fichier DEF. La liste d’exportation pour *`MFCxx.DLL`* et les dll d’extension OLE et de base de données, plusieurs milliers de fois, ont été générées avec un processus de ce type (bien qu’elle ne soit pas entièrement automatique et nécessite un réglage manuel chaque fois dans un moment).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp et CDynLinkLibrary

Une DLL d’extension MFC ne dispose pas `CWinApp` d’un objet dérivé de. Au lieu de cela, il doit fonctionner avec l' `CWinApp` objet dérivé de l’application cliente. Cela signifie que l’application cliente possède la pompe de messages principale, la boucle inactive, et ainsi de suite.

Si votre DLL d’extension MFC doit gérer des données supplémentaires pour chaque application, vous pouvez dériver une nouvelle classe de `CDynLinkLibrary` et la créer dans la `InitXxxDLL` routine décrite ci-dessus. Lors de son exécution, la DLL peut vérifier la liste d’objets de l’application actuelle `CDynLinkLibrary` pour trouver celle correspondant à cette DLL d’extension MFC.

### <a name="using-resources-in-your-dll-implementation"></a>Utilisation des ressources dans votre implémentation de DLL

Comme indiqué ci-dessus, le chargement de ressources par défaut parcourt la liste des `CDynLinkLibrary` objets qui recherchent le premier fichier exe ou dll qui a la ressource demandée. Toutes les API MFC et le code interne utilisent `AfxFindResourceHandle` pour parcourir la liste des ressources et rechercher n’importe quelle ressource, quel que soit l’emplacement où elles se trouvent.

Si vous souhaitez uniquement charger des ressources à partir d’un emplacement spécifique, utilisez les API `AfxGetResourceHandle` et `AfxSetResourceHandle` pour enregistrer l’ancien descripteur et définir le nouveau descripteur. Veillez à restaurer l’ancien handle de ressource avant de revenir à l’application cliente. L’exemple de TESTDLL2 utilise cette approche pour le chargement explicite d’un menu.

Le parcours de la liste présente quelques inconvénients : il est légèrement plus lent et requiert la gestion des plages d’ID de ressource. Il présente l’avantage qu’une application cliente liée à plusieurs DLL d’extension MFC peut utiliser n’importe quelle ressource fournie par la DLL sans devoir spécifier le descripteur d’instance de DLL. `AfxFindResourceHandle` API utilisée pour parcourir la liste des ressources afin de rechercher une correspondance donnée. Il prend le nom et le type d’une ressource et retourne le handle de ressource où il trouve d’abord la ressource, ou NULL.

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Écriture d’une application qui utilise la version de la DLL

### <a name="application-requirements"></a>Configuration requise pour l’application

Une application qui utilise la version partagée de MFC doit suivre quelques règles de base :

- Il doit avoir un `CWinApp` objet et suivre les règles standard pour une pompe de messages.

- Elle doit être compilée avec un ensemble d’indicateurs de compilateur requis (voir ci-dessous).

- Elle doit être liée aux bibliothèques d’importation MFCxx. En définissant les indicateurs requis du compilateur, les en-têtes MFC déterminent au moment de la liaison la bibliothèque avec laquelle l’application doit établir une liaison.

- Pour exécuter le fichier exécutable, *`MFCxx.DLL`* doit se trouver sur le chemin d’accès ou dans le répertoire système de Windows.

### <a name="building-with-the-development-environment"></a>Création avec l’environnement de développement

Si vous utilisez le Makefile interne avec la plupart des valeurs par défaut standard, vous pouvez facilement modifier le projet pour générer la version de la DLL.

L’étape suivante suppose que vous disposez d’une application MFC correctement opérationnelle liée à *`NAFXCWD.LIB`* (pour le débogage) et *`NAFXCW.LIB`* (pour la version) et que vous souhaitez la convertir pour utiliser la version partagée de la bibliothèque MFC. Vous exécutez l’environnement Visual Studio et avez un fichier projet interne.

1. Dans le menu **projets** , sélectionnez **Propriétés**. Dans la page **général** , sous **paramètres par défaut du projet**, définissez Microsoft Foundation classes pour **utiliser MFC dans une DLL partagée** (MFCxx (d). dll).

### <a name="building-with-nmake"></a>Génération avec NMAKE

Si vous utilisez la fonctionnalité de Makefile externe du compilateur, ou si vous utilisez NMAKE directement, vous devrez modifier votre makefile pour prendre en charge les options de compilateur et de l’éditeur de liens requises.

Indicateurs requis du compilateur :

- **`/D_AFXDLL /MD`**
  **`/D_AFXDLL`**

Les en-têtes MFC standard nécessitent la `_AFXDLL` définition du symbole.

- **`/MD`** L’application doit utiliser la version DLL de la bibliothèque Runtime C.

Tous les autres indicateurs de compilateur suivent les valeurs par défaut MFC (par exemple, `_DEBUG` pour le débogage).

Modifiez la liste des bibliothèques de l’éditeur de liens. Remplacez *`NAFXCWD.LIB`* par *`MFCxxD.LIB`* et *`NAFXCW.LIB`* *`MFCxx.LIB`* . Remplacez *`LIBC.LIB`* par *`MSVCRT.LIB`* . Comme pour toute autre bibliothèque MFC, il est important que *`MFCxxD.LIB`* soit placé **avant** les bibliothèques Runtime C.

Ajoutez éventuellement **`/D_AFXDLL`** à vos options de compilateur de ressources de mise en sortie et de débogage (celui qui compile réellement les ressources avec **`/R`** ). Cette option permet de réduire la taille de l’exécutable final en partageant les ressources qui sont présentes dans les DLL MFC.

Une régénération complète est nécessaire une fois que ces modifications ont été effectuées.

### <a name="building-the-samples"></a>Génération des exemples

La plupart des exemples de programmes MFC peuvent être générés à partir d’Visual C++ ou d’un MAKEFILE partagé basé sur NMAKE à partir de la ligne de commande.

Pour convertir l’un de ces exemples à utiliser *`MFCxx.DLL`* , vous pouvez charger le fichier Mak dans le Visual C++ et définir les options du projet, comme décrit ci-dessus. Si vous utilisez la build NMAKE, vous pouvez spécifier `AFXDLL=1` sur la ligne de commande NMAKE et générer l’exemple à l’aide des bibliothèques MFC partagées.

L’exemple de concepts avancés MFC [DLLHUSK](../overview/visual-cpp-samples.md) est généré avec la version DLL de MFC. Cet exemple illustre non seulement comment créer une application liée à *`MFCxx.DLL`* , mais il illustre également d’autres fonctionnalités de l’option d’empaquetage de DLL MFC telles que les dll d’extension MFC décrites plus loin dans cette note technique.

### <a name="packaging-notes"></a>Notes de Packaging

Les versions Release des dll ( *`MFCxx.DLL`* et *`MFCxxU.DLL`* ) sont redistribuables librement. Les versions Debug des dll ne sont pas redistribuables librement et doivent être utilisées uniquement pendant le développement de votre application.

Les dll de débogage sont fournies avec des informations de débogage. En utilisant le débogueur Visual C++, vous pouvez suivre l’exécution de votre application et de la DLL. Les dll de mise en sortie ( *`MFCxx.DLL`* et *`MFCxxU.DLL`* ) ne contiennent pas d’informations de débogage.

Si vous personnalisez ou régénérez les dll, vous devez les appeler autre chose que « MFCxx ». Le fichier SRC MFC *`MFCDLL.MAK`* décrit les options de génération et contient la logique de changement de nom de la dll. Le changement de nom des fichiers est nécessaire, car ces dll sont potentiellement partagées par de nombreuses applications MFC. Le fait de faire en sorte que votre version personnalisée des DLL MFC remplace celles installées sur le système peut bloquer une autre application MFC à l’aide des DLL MFC partagées.

La reconstruction des DLL MFC n’est pas recommandée.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Comment l' MFCxx.DLL est implémentée

La section suivante décrit comment la DLL MFC ( *`MFCxx.DLL`* et *`MFCxxD.DLL`* ) est implémentée. La compréhension des détails ici n’est pas non plus importante si vous voulez utiliser la DLL MFC avec votre application. Les détails ici ne sont pas essentiels pour comprendre comment écrire une DLL d’extension MFC, mais la compréhension de cette implémentation peut vous aider à écrire votre propre DLL.

### <a name="implementation-overview"></a>Vue d’ensemble de l’implémentation

La DLL MFC est en réalité un cas spécial d’une DLL d’extension MFC, comme décrit ci-dessus. Il a un grand nombre d’exportations pour un grand nombre de classes. Nous faisons quelques opérations supplémentaires dans la DLL MFC qui la rendent encore plus spéciale qu’une DLL d’extension MFC standard.

### <a name="win32-does-most-of-the-work"></a>Win32 effectue la majeure partie du travail

La version 16 bits de MFC nécessitait un certain nombre de techniques spéciales, notamment les données par application sur le segment de pile, les segments spéciaux créés par un code assembleur 80x86, les contextes d’exception par processus et d’autres techniques. Win32 prend directement en charge les données par processus dans une DLL, ce que vous souhaitez la plupart du temps. Pour l’essentiel *`MFCxx.DLL`* , il est simplement *`NAFXCW.LIB`* empaqueté dans une dll. Si vous examinez le code source MFC, vous trouverez peu de `#ifdef _AFXDLL` cas, car il n’y a pas beaucoup de cas particuliers qui doivent être faits. Les cas spéciaux qui sont spécifiques à la gestion de Win32 sur Windows 3,1 (également connu sous le nom de Win32s). Win32s ne prend pas en charge directement les données DLL par processus. La DLL MFC doit utiliser les API de stockage local des threads (TLS) Win32 pour obtenir les données locales du processus.

### <a name="impact-on-library-sources-additional-files"></a>Impact sur les sources de bibliothèque, fichiers supplémentaires

L’impact de la `_AFXDLL` version sur les sources et en-têtes de la bibliothèque de classes MFC normale est relativement mineur. Un fichier de version spécial ( *`AFXV_DLL.H`* ) et un fichier d’en-tête supplémentaire ( *`AFXDLL_.H`* ) sont inclus dans l' *`AFXWIN.H`* en-tête principal. L' *`AFXDLL_.H`* en-tête comprend la `CDynLinkLibrary` classe et d’autres détails d’implémentation des `_AFXDLL` applications et des dll d’extension MFC. L' *`AFXDLLX.H`* en-tête est fourni pour générer des dll d’extension MFC (voir ci-dessus pour plus d’informations).

Les sources standard de la bibliothèque MFC dans la source de code MFC contiennent du code conditionnel supplémentaire sous le `_AFXDLL` #ifdef. Un fichier source supplémentaire ( *`DLLINIT.CPP`* ) contient le code d’initialisation de la dll supplémentaire et un autre Glue pour la version partagée de MFC.

Pour générer la version partagée de MFC, des fichiers supplémentaires sont fournis. (Voir ci-dessous pour plus d’informations sur la génération de la DLL.)

- Deux fichiers DEF sont utilisés pour exporter les points d’entrée de DLL MFC pour les versions Debug ( *`MFCxxD.DEF`* ) et Release ( *`MFCxx.DEF`* ) de la dll.

- Un fichier RC ( *`MFCDLL.RC`* ) contient toutes les ressources MFC standard et une `VERSIONINFO` ressource pour la dll.

- Un fichier CLW ( *`MFCDLL.CLW`* ) est fourni pour permettre l’exploration des classes MFC à l’aide de ClassWizard. Cette fonctionnalité n’est pas spécifique à la version DLL de MFC.

### <a name="memory-management"></a>Gestion de la mémoire

Une application utilisant *`MFCxx.DLL`* utilise un allocateur de mémoire commun fourni par *`MSVCRTxx.DLL`* , la dll du runtime C partagé. L’application, toutes les dll d’extension MFC, ainsi que les DLL MFC utilisent cet allocateur de mémoire partagée. En utilisant une DLL partagée pour l’allocation de mémoire, les DLL MFC peuvent allouer de la mémoire qui est libérée par la suite par l’application ou vice versa. Étant donné que l’application et la DLL doivent utiliser le même allocateur, vous ne devez pas substituer le C++ global **`operator new`** ou **`operator delete`** . Les mêmes règles s’appliquent au reste des routines d’allocation de mémoire Runtime C (telles que `malloc` , `realloc` , `free` et autres).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Ordinaux et classe __declspec (dllexport) et nom de la DLL

Nous n’utilisons pas les `class` **`__declspec(dllexport)`** fonctionnalités du compilateur C++. Au lieu de cela, une liste d’exportations est incluse avec les sources de la bibliothèque de classes ( *`MFCxx.DEF`* et *`MFCxxD.DEF`* ). Seul un ensemble SELECT de points d’entrée (fonctions et données) est exporté. Les autres symboles, tels que les classes ou les fonctions d’implémentation privée MFC, ne sont pas exportés. Toutes les exportations sont effectuées par ordinal sans nom de chaîne dans la table de noms résidents ou non résidents.

L’utilisation `class` **`__declspec(dllexport)`** de peut être une alternative viable pour la génération de dll plus petites, mais dans une dll volumineuse comme MFC, le mécanisme d’exportation par défaut a des limites d’efficacité et de capacité.

Ce que cela signifie, c’est que nous pouvons empaqueter une grande quantité de fonctionnalités dans la version d' *`MFCxx.DLL`* environ 800 Ko sans compromettre beaucoup l’exécution ou la vitesse de chargement. *`MFCxx.DLL`* aurait été de 100 Ko plus grand si cette technique n’était pas utilisée. La technique permet d’ajouter des points d’entrée supplémentaires à la fin du fichier DEF. Il permet un contrôle de version simple sans compromettre la vitesse et l’efficacité de la taille de l’exportation par ordinal. Les révisions majeures de la version de la bibliothèque de classes MFC modifient le nom de la bibliothèque. Autrement dit, *`MFC30.DLL`* est la dll redistribuable contenant la version 3,0 de la bibliothèque de classes MFC. Une mise à niveau de cette DLL, par exemple, dans une hypothétique MFC 3,1, la DLL serait nommée à la *`MFC31.DLL`* place. Là encore, si vous modifiez le code source MFC pour produire une version personnalisée de la DLL MFC, utilisez un nom différent (et de préférence un sans « MFC » dans le nom).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
