---
title: 'TN033 : version DLL de MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: c627f891efc893f4eb8dae4bfb0b3b78f7af1a46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215931"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033 : version DLL de MFC

Cette note décrit comment vous pouvez utiliser les bibliothèques de liens dynamiques partagées MFCxx.DLL et MFCxxD.DLL (où x est le numéro de version MFC) avec les applications MFC et les dll d’extension MFC. Pour plus d’informations sur les DLL MFC standard, consultez [utilisation de MFC dans le cadre d’une dll](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Cette note technique couvre trois aspects des dll. Les deux derniers sont destinés aux utilisateurs les plus avancés :

- [Comment créer une DLL d’extension MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Comment créer une application MFC qui utilise la version DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Comment les bibliothèques de liens dynamiques partagées MFC sont implémentées](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Si vous souhaitez créer une DLL à l’aide de MFC qui peut être utilisée avec des applications non-MFC (il s’agit d’une DLL MFC standard), reportez-vous à la [note technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Vue d’ensemble de la prise en charge de MFCxx.DLL : terminologie et fichiers

**DLL MFC normale**: vous utilisez une DLL MFC normale pour générer une dll autonome à l’aide de certaines des classes MFC. Les interfaces à travers les limites de l’application/DLL sont des interfaces « C », et l’application cliente ne doit pas nécessairement être une application MFC.

Il s’agit de la version de la prise en charge des DLL prise en charge dans MFC 1,0. Il est décrit dans [Technical Note 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) et MFC Advanced concepts Sample [DLLScreenCap](../overview/visual-cpp-samples.md).

> [!NOTE]
> À partir de Visual C++ version 4,0, le terme **USRDLL** est obsolète et a été remplacé par une DLL MFC normale qui est liée de manière statique aux MFC. Vous pouvez également générer une DLL MFC normale qui est liée de manière dynamique aux MFC.

MFC 3,0 (et versions ultérieures) prend en charge les DLL MFC classiques avec toutes les nouvelles fonctionnalités, notamment les classes OLE et de base de données.

**AFXDLL**: c’est ce que l’on appelle également la version partagée des bibliothèques MFC. Il s’agit de la nouvelle prise en charge des DLL ajoutée dans MFC 2,0. La bibliothèque MFC elle-même se trouve dans un certain nombre de dll (décrites ci-dessous) et une application cliente ou une DLL relie dynamiquement les dll dont elle a besoin. Les interfaces entre les limites d’application/DLL sont des interfaces de classe C++/MFC. L’application cliente doit être une application MFC. Cela prend en charge toutes les fonctionnalités MFC 3,0 (exception : UNICODE n’est pas pris en charge pour les classes de base de données).

> [!NOTE]
> À partir de Visual C++ version 4,0, ce type de DLL est appelé « DLL d’extension ».

Cette remarque utilisera MFCxx.DLL pour faire référence à l’ensemble de la DLL MFC, qui comprend :

- Débogage : MFCxxD.DLL (combiné) et MFCSxxD. LIB (statique).

- Version : MFCxx.DLL (combiné) et MFCSxx. LIB (statique).

- Débogage Unicode : MFCxxUD.DLL (combiné) et MFCSxxD. LIB (statique).

- Version Unicode : MFCxxU.DLL (combiné) et MFCSxxU. LIB (statique).

> [!NOTE]
> MFCSxx [U] [D]. Les bibliothèques LIB sont utilisées conjointement avec les DLL partagées MFC. Ces bibliothèques contiennent du code qui doit être lié de manière statique à l’application ou à la DLL.

Une application est liée aux bibliothèques d’importation correspondantes :

- Débogage : MFCxxD. LIB

- Version : MFCxx. LIB

- Débogage Unicode : MFCxxUD. LIB

- Version Unicode : MFCxxU. LIB

Une « DLL d’extension MFC » est une DLL générée à partir de MFCxx.DLL (et/ou d’autres DLL partagées MFC). Ici, l’architecture des composants MFC démarre. Si vous dérivez une classe utile d’une classe MFC ou si vous créez une autre boîte à outils de type MFC, vous pouvez la placer dans une DLL. Cette DLL utilise MFCxx.DLL, comme l’application cliente ultime. Cela permet des classes feuille réutilisables, des classes de base réutilisables et des vues/classes de document réutilisables.

## <a name="pros-and-cons"></a>Avantages et inconvénients

Pourquoi utiliser la version partagée de MFC ?

- L’utilisation de la bibliothèque partagée peut entraîner des applications plus petites (une application minimale qui utilise la plupart de la bibliothèque MFC est inférieure à 10 Ko).

- La version partagée de MFC prend en charge les dll d’extension MFC et les DLL MFC standard.

- La création d’une application qui utilise les bibliothèques MFC partagées est plus rapide que la création d’une application MFC liée de manière statique, car il n’est pas nécessaire de lier la bibliothèque MFC elle-même. Cela est particulièrement vrai dans les versions **Debug** où l’éditeur de liens doit compacter les informations de débogage : en créant une liaison avec une dll qui contient déjà les informations de débogage, il y a moins d’informations de débogage à compacter dans votre application.

Pourquoi ne pas utiliser la version partagée de MFC :

- L’expédition d’une application qui utilise la bibliothèque partagée nécessite que vous livriez la bibliothèque MFCxx.DLL (et autres) avec votre programme. MFCxx.DLL est redistribuable librement comme de nombreuses dll, mais vous devez toujours installer la DLL dans votre programme d’installation. En outre, vous devez expédier le MSVCRTxx.DLL, qui contient la bibliothèque Runtime C qui est utilisée à la fois par votre programme et les DLL MFC elles-mêmes.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Comment écrire une DLL d’extension MFC

Une DLL d’extension MFC est une DLL qui contient des classes et des fonctions écrites pour embellir les fonctionnalités des classes MFC. Une DLL d’extension MFC utilise les DLL MFC partagées de la même façon qu’une application l’utilise, avec quelques considérations supplémentaires :

- Le processus de génération est semblable à la création d’une application qui utilise les bibliothèques MFC partagées avec quelques options supplémentaires du compilateur et de l’éditeur de liens.

- Une DLL d’extension MFC n’a pas de `CWinApp` classe dérivée de.

- Une DLL d’extension MFC doit fournir un spécial `DllMain` . AppWizard fournit une `DllMain` fonction que vous pouvez modifier.

- Une DLL d’extension MFC fournit généralement une routine d’initialisation pour créer un `CDynLinkLibrary` si la dll d’extension MFC souhaite exporter `CRuntimeClass` es ou des ressources vers l’application. Une classe dérivée de `CDynLinkLibrary` peut être utilisée si les données par application doivent être gérées par la dll d’extension MFC.

Ces considérations sont décrites plus en détail ci-dessous. Vous devez également vous référer à l’exemple de concepts avancés MFC [DLLHUSK](../overview/visual-cpp-samples.md) , car il illustre les éléments suivants :

- Génération d’une application à l’aide des bibliothèques partagées. (DLLHUSK.EXE est une application MFC qui est liée de manière dynamique aux bibliothèques MFC, ainsi qu’à d’autres dll.)

- Génération d’une DLL d’extension MFC. (Notez les indicateurs spéciaux, tels que, `_AFXEXT` qui sont utilisés lors de la génération d’une DLL d’extension MFC)

- Deux exemples de DLL d’extension MFC. L’une d’elles illustre la structure de base d’une DLL d’extension MFC avec des exportations limitées (TESTDLL1) et l’autre montre l’exportation d’une interface de classe entière (TESTDLL2).

L’application cliente et toutes les dll d’extension MFC doivent utiliser la même version de MFCxx.DLL. Vous devez suivre la Convention de la DLL MFC et fournir une version Debug et une version commerciale (/Release) de votre DLL d’extension MFC. Cela permet aux programmes clients de générer à la fois des versions de débogage et des versions commerciales de leurs applications et de les lier à la version Debug ou commerciale appropriée de toutes les dll.

> [!NOTE]
> Dans la mesure où les problèmes de gestion et d’exportation des noms C++, la liste d’exportation à partir d’une DLL d’extension MFC peut être différente entre les versions Debug et version commerciale de la même DLL et des dll pour différentes plateformes. Le MFCxx.DLL de vente au détail dispose d’environ 2000 points d’entrée exportés ; le MFCxxD.DLL de débogage a environ 3000 points d’entrée exportés.

### <a name="quick-note-on-memory-management"></a>Note rapide sur la gestion de la mémoire

La section intitulée « gestion de la mémoire », vers la fin de cette note technique, décrit l’implémentation de la MFCxx.DLL avec la version partagée de MFC. Les informations que vous devez connaître pour implémenter uniquement une DLL d’extension MFC sont décrites ici.

MFCxx.DLL et toutes les dll d’extension MFC chargées dans l’espace d’adressage d’une application cliente utiliseront le même allocateur de mémoire, le chargement des ressources et d’autres États « globaux » MFC comme s’ils se trouvaient dans la même application. Cela est important, car les bibliothèques DLL non-MFC et les DLL MFC régulières liées de manière statique aux MFC font exactement le contraire et ont chaque DLL allouée à partir de son propre pool de mémoire.

Si une DLL d’extension MFC alloue de la mémoire, cette mémoire peut être mélangée librement avec tout autre objet alloué par l’application. En outre, si une application qui utilise les bibliothèques MFC partagées se bloque, la protection du système d’exploitation conserve l’intégrité de toute autre application MFC qui partage la DLL.

De même que d’autres États MFC « globaux », comme le fichier exécutable actuel à partir duquel charger des ressources, sont également partagés entre l’application cliente et toutes les dll d’extension MFC, ainsi que MFCxx.DLL elles-mêmes.

### <a name="building-an-mfc-extension-dll"></a>Génération d’une DLL d’extension MFC

Vous pouvez utiliser AppWizard pour créer un projet de DLL d’extension MFC et générer automatiquement les paramètres de compilateur et de l’éditeur de liens appropriés. Il a également généré une `DllMain` fonction que vous pouvez modifier.

Si vous convertissez un projet existant en DLL d’extension MFC, commencez par les règles standard de génération d’une application à l’aide de la version partagée de MFC, puis procédez comme suit :

- Ajoutez **/D_AFXEXT** aux indicateurs du compilateur. Dans la boîte de dialogue Propriétés du projet, sélectionnez le nœud C/C++. Sélectionnez ensuite la catégorie préprocesseur. Ajoutez `_AFXEXT` au champ définir des macros, en séparant chacun des éléments par des points-virgules.

- Supprimez le commutateur de compilateur **/Gy** . Dans la boîte de dialogue Propriétés du projet, sélectionnez le nœud C/C++. Sélectionnez ensuite la catégorie génération de code. Assurez-vous que l’option « Activer la liaison au niveau des fonctions » n’est pas activée. Cela facilitera l’exportation des classes, car l’éditeur de liens ne supprimera pas les fonctions non référencées. Si le projet d’origine est utilisé pour générer une DLL MFC normale liée de manière statique aux MFC, remplacez l’option de compilateur **/MT [d]** par **/MD [d]**.

- Générez une bibliothèque d’exportation avec l’option **/dll** à lier. Cette valeur est définie lorsque vous créez une cible, en spécifiant la bibliothèque de liens dynamiques Win32 comme type de cible.

### <a name="changing-your-header-files"></a>Modification de vos fichiers d’en-tête

L’objectif d’une DLL d’extension MFC est généralement d’exporter des fonctionnalités communes vers une ou plusieurs applications qui peuvent utiliser cette fonctionnalité. Cela revient à exporter des classes et des fonctions globales qui sont disponibles pour vos applications clientes.

Pour ce faire, vous devez vous assurer que chacune des fonctions membres est marquée comme importation ou exportation, le cas échéant. Cela nécessite des déclarations spéciales : `__declspec(dllexport)` et `__declspec(dllimport)` . Quand vos classes sont utilisées par les applications clientes, vous souhaitez qu’elles soient déclarées comme `__declspec(dllimport)` . Lorsque la DLL d’extension MFC est créée, elle doit être déclarée comme `__declspec(dllexport)` . En outre, les fonctions doivent être exportées, de sorte que les programmes clients s’y lient au moment du chargement.

Pour exporter votre classe entière, utilisez `AFX_EXT_CLASS` dans la définition de classe. Cette macro est définie par l’infrastructure comme `__declspec(dllexport)` lorsque `_AFXDLL` et `_AFXEXT` est défini, mais défini comme `__declspec(dllimport)` lorsque `_AFXEXT` n’est pas défini. `_AFXEXT`comme décrit ci-dessus, est défini uniquement lors de la génération de votre DLL d’extension MFC. Par exemple :

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Non-exportation de la classe entière

Il peut arriver que vous souhaitiez exporter uniquement les membres nécessaires individuels de votre classe. Par exemple, si vous exportez une `CDialog` classe dérivée de, vous devrez peut-être exporter le constructeur et l' `DoModal` appel. Vous pouvez exporter ces membres à l’aide de la DLL. Fichier DEF, mais vous pouvez également utiliser à `AFX_EXT_CLASS` peu près de la même façon sur les membres individuels que vous devez exporter.

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

Dans ce cas, vous risquez de rencontrer un problème supplémentaire, car vous n’exportez plus tous les membres de la classe. Le problème est lié à la façon dont les macros MFC fonctionnent. Plusieurs macros d’assistance MFC déclarent ou définissent en fait des membres de données. Par conséquent, ces membres de données devront également être exportés à partir de votre DLL.

Par exemple, la macro DECLARE_DYNAMIC est définie comme suit lors de la génération d’une DLL d’extension MFC :

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

La ligne qui commence « static `AFX_DATA` » déclare un objet statique à l’intérieur de votre classe. Pour exporter cette classe correctement et accéder aux informations d’exécution à partir d’un client. EXE, vous devez exporter cet objet statique. Étant donné que l’objet statique est déclaré avec le modificateur `AFX_DATA` , vous devez uniquement définir `AFX_DATA` comme étant lors de la `__declspec(dllexport)` génération de votre dll et le définir comme `__declspec(dllimport)` lors de la génération de votre exécutable client.

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

Vous pouvez utiliser la même technique pour exporter automatiquement l' `CArchive` opérateur d’extraction pour les classes qui utilisent les macros DECLARE_SERIAL et IMPLEMENT_SERIAL. Exportez l’opérateur d’archive en délimitant les déclarations de classe (situées dans le. Fichier H) avec le code suivant :

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Limitations de _AFXEXT

Vous pouvez utiliser le symbole de préprocesseur _**AFXEXT** pour vos dll d’extension MFC tant que vous n’avez pas plusieurs couches de DLL d’extension MFC. Si vous avez des dll d’extension MFC qui appellent ou dérivent de classes dans vos propres DLL d’extension MFC, qui dérivent ensuite des classes MFC, vous devez utiliser votre propre symbole de préprocesseur pour éviter toute ambiguïté.

Le problème est que dans Win32, vous devez déclarer explicitement toutes les données comme `__declspec(dllexport)` si elles étaient exportées à partir d’une dll, et `__declspec(dllimport)` si elles doivent être importées à partir d’une dll. Lorsque vous définissez `_AFXEXT` , les en-têtes MFC s’assurent que `AFX_EXT_CLASS` est défini correctement.

Lorsque vous avez plusieurs couches, un symbole tel que `AFX_EXT_CLASS` n’est pas suffisant, car une DLL d’extension MFC peut exporter de nouvelles classes et importer d’autres classes à partir d’une autre DLL d’extension MFC. Pour résoudre ce problème, utilisez un symbole de préprocesseur spécial qui indique que vous générez la DLL et que vous utilisez la DLL. Par exemple, Imaginez deux DLL d’extension MFC, A.DLL et B.DLL. Chacun exporte des classes dans A. H et B. H, respectivement. B.DLL utilise les classes de A.DLL. Les fichiers d’en-tête ressemblent à ceci :

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

Lorsque A.DLL est créé, il est généré avec **/DA_IMPL** et, lorsque B.DLL est créé, il est généré avec **/DB_IMPL**. En utilisant des symboles distincts pour chaque DLL, CExampleB est exporté et CExampleA est importé lors de la génération de B.DLL. CExampleA est exporté lors de la génération de A.DLL et importé lorsqu’il est utilisé par B.DLL (ou un autre client).

Ce type de superposition ne peut pas être effectué lors de l’utilisation `AFX_EXT_CLASS` des `_AFXEXT` symboles de préprocesseur intégrés et. La technique décrite ci-dessus résout ce problème d’une manière qui ne diffère pas du mécanisme que MFC utilise lui-même lors de la création de ses dll d’extension OLE, de base de données et de réseau.

### <a name="not-exporting-the-entire-class"></a>Non-exportation de la classe entière

Là encore, vous devez faire particulièrement attention lorsque vous n’exportez pas une classe entière. Vous devez vous assurer que les éléments de données nécessaires créés par les macros MFC sont exportés correctement. Pour ce faire, vous pouvez redéfinir `AFX_DATA` la macro de votre classe spécifique. Cela doit être fait à chaque fois que vous n’exportez pas la classe entière.

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

Voici le code exact que vous devez placer dans votre fichier source principal pour votre DLL d’extension MFC. Il doit venir après les inclusions standard. Notez que lorsque vous utilisez AppWizard pour créer des fichiers de démarrage pour une DLL d’extension MFC, il fournit un `DllMain` pour vous.

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

L’appel de `AfxInitExtensionModule` capture les classes Runtime ( `CRuntimeClass` structures) des modules, ainsi que ses fabriques d’objets ( `COleObjectFactory` objets) pour une utilisation ultérieure lors de la création de l' `CDynLinkLibrary` objet. L’appel (facultatif) `AfxTermExtensionModule` permet à MFC de nettoyer la dll d’extension MFC lorsque chaque processus se détache (ce qui se produit lorsque le processus se termine, ou lorsque la dll est déchargée suite `FreeLibrary` à un appel) de la dll d’extension MFC. Étant donné que la plupart des dll d’extension MFC ne sont pas chargées dynamiquement (généralement, elles sont liées via leurs bibliothèques d’importation), l’appel à `AfxTermExtensionModule` n’est généralement pas nécessaire.

Si votre application charge et libère des dll d’extension MFC de manière dynamique, veillez à appeler `AfxTermExtensionModule` comme indiqué ci-dessus. Veillez également à utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions `LoadLibrary` Win32 `FreeLibrary` et) si votre application utilise plusieurs threads ou si elle charge dynamiquement une DLL d’extension MFC. L’utilisation `AfxLoadLibrary` de et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la dll d’extension MFC est chargée et déchargée n’endommage pas l’état global des MFC.

Fichier d’en-tête AFXDLLX. H contient des définitions spéciales pour les structures utilisées dans les dll d’extension MFC, telles que la définition de `AFX_EXTENSION_MODULE` et `CDynLinkLibrary` .

Le *extensionDLL* global doit être déclaré comme indiqué. Contrairement à la version 16 bits de MFC, vous pouvez allouer de la mémoire et appeler des fonctions MFC pendant ce temps, puisque la MFCxx.DLL est entièrement initialisée au moment de l' `DllMain` appel de.

### <a name="sharing-resources-and-classes"></a>Partage des ressources et des classes

Les dll d’extension MFC simples doivent uniquement exporter quelques fonctions à faible bande passante vers l’application cliente, et rien de plus. D’autres dll gourmandes en interface utilisateur peuvent souhaiter exporter des ressources et des classes C++ vers l’application cliente.

L’exportation des ressources s’effectue par le biais d’une liste de ressources. Dans chaque application correspond une liste d’objets liée de façon unique `CDynLinkLibrary` . Lors de la recherche d’une ressource, la plupart des implémentations MFC standard qui chargent les ressources s’affichent d’abord dans le module de ressource en cours ( `AfxGetResourceHandle` ) et, si elles ne sont pas trouvées, parcourent la liste des `CDynLinkLibrary` objets tentant de charger la ressource demandée.

La création dynamique d’objets C++ en fonction d’un nom de classe C++ est similaire. Le mécanisme de désérialisation des objets MFC doit avoir tous les objets inscrits pour pouvoir être `CRuntimeClass` reconstruit en créant de manière dynamique l’objet C++ du type requis en fonction de ce qui a été stocké précédemment.

Si vous souhaitez que l’application cliente utilise des classes de votre DLL d’extension MFC qui sont `DECLARE_SERIAL` , vous devez exporter vos classes pour qu’elles soient visibles par l’application cliente. Cela s’effectue également en parcourant la `CDynLinkLibrary` liste.

Dans le cas de l’exemple de concepts avancés MFC [DLLHUSK](../overview/visual-cpp-samples.md), la liste ressemble à ceci :

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

Le MFCxx.DLL est généralement en dernier dans la liste des ressources et des classes. MFCxx.DLL inclut toutes les ressources MFC standard, y compris les chaînes de demande pour tous les ID de commande standard. Le fait de le placer à la fin de la liste permet aux dll et à l’application cliente de ne pas avoir leur propre copie des ressources MFC standard, mais de s’appuyer sur les ressources partagées dans le MFCxx.DLL à la place.

La fusion des ressources et des noms de classes de toutes les dll dans l’espace de noms de l’application cliente présente l’inconvénient que vous devez faire attention aux ID ou noms que vous choisissez. Vous pouvez bien sûr désactiver cette fonctionnalité en n’exportant ni vos ressources, ni un `CDynLinkLibrary` objet vers l’application cliente. L’exemple [DLLHUSK](../overview/visual-cpp-samples.md) gère l’espace de noms de ressources partagées à l’aide de plusieurs fichiers d’en-tête. Pour plus d’informations sur l’utilisation des fichiers de ressources partagées, consultez la [note technique 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) .

### <a name="initializing-the-dll"></a>Initialisation de la DLL

Comme indiqué ci-dessus, vous souhaiterez généralement créer un `CDynLinkLibrary` objet afin d’exporter vos ressources et classes vers l’application cliente. Vous devrez fournir un point d’entrée exporté pour initialiser la DLL. Au minimum, il s’agit d’une routine void qui ne prend pas d’arguments et ne retourne rien, mais il peut s’agir de tout ce que vous aimez.

Chaque application cliente qui souhaite utiliser votre DLL doit appeler cette routine d’initialisation, si vous utilisez cette approche. Vous pouvez également allouer cet `CDynLinkLibrary` objet dans votre `DllMain` juste après l’appel de `AfxInitExtensionModule` .

La routine d’initialisation doit créer un `CDynLinkLibrary` objet dans le tas de l’application actuelle, connecté à vos informations de DLL d’extension MFC. Pour ce faire, vous pouvez effectuer les opérations suivantes :

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Le nom de la routine, *InitXxxDLL* dans cet exemple, peut être tout ce que vous souhaitez. Elle n’a pas besoin d’être **extern "C"**, mais cela rend la liste d’exportation plus facile à gérer.

> [!NOTE]
> Si vous utilisez votre DLL d’extension MFC à partir d’une DLL MFC normale, vous devez exporter cette fonction d’initialisation. Cette fonction doit être appelée à partir de la DLL MFC normale avant d’utiliser des classes ou des ressources DLL d’extension MFC.

### <a name="exporting-entries"></a>Exportation d’entrées

Le moyen le plus simple d’exporter vos classes consiste à utiliser `__declspec(dllimport)` et `__declspec(dllexport)` sur chaque classe et fonction globale que vous souhaitez exporter. Cela simplifie considérablement la tâche, mais est moins efficace que le nom de chaque point d’entrée (décrit ci-dessous), car vous avez moins de contrôle sur les fonctions exportées et vous ne pouvez pas exporter les fonctions par ordinal. TESTDLL1 et TESTDLL2 utilisent cette méthode pour exporter leurs entrées.

Une méthode plus efficace (et la méthode utilisée par MFCxx.DLL) consiste à exporter chaque entrée manuellement en nommant chaque entrée dans le. Fichier DEF. Étant donné que nous exportons des exportations sélectives à partir de notre DLL (autrement dit, pas tout), nous devons décider quelles interfaces particulières nous souhaitons exporter. Cela est difficile, car vous devez spécifier les noms tronqués à l’éditeur de liens sous la forme d’entrées dans le. Fichier DEF. N’exportez pas de classes C++, sauf si vous avez vraiment besoin d’un lien symbolique pour celle-ci.

Si vous avez essayé d’exporter des classes C++ avec un. Fichier DEF avant, vous souhaiterez peut-être développer un outil pour générer automatiquement cette liste. Cela peut être fait à l’aide d’un processus de liaison en deux étapes. Liez une seule fois votre DLL à aucune exportation et autorisez l’éditeur de liens à générer un. Fichier de mappage. La. Le fichier de mappage peut être utilisé pour générer une liste de fonctions qui doivent être exportées, de sorte qu’en cas de réorganisation, il peut être utilisé pour générer vos entrées d’exportation pour votre. Fichier DEF. La liste d’exportation pour les MFCxx.DLL et les dll d’extension OLE et de base de données, plusieurs milliers de nombre, a été générée avec un processus de ce type (bien qu’elle ne soit pas complètement automatique et nécessite un réglage manuel chaque fois dans un moment).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp et CDynLinkLibrary

Une DLL d’extension MFC n’a pas `CWinApp` d’objet dérivé de qui lui est propre. elle doit plutôt fonctionner avec l' `CWinApp` objet dérivé de l’application cliente. Cela signifie que l’application cliente possède la pompe de messages principale, la boucle inactive, etc.

Si votre DLL d’extension MFC doit gérer des données supplémentaires pour chaque application, vous pouvez dériver une nouvelle classe de `CDynLinkLibrary` et la créer dans la routine InitXxxDLL décrite ci-dessus. Lors de son exécution, la DLL peut vérifier la liste d’objets de l’application actuelle `CDynLinkLibrary` pour trouver celle correspondant à cette DLL d’extension MFC.

### <a name="using-resources-in-your-dll-implementation"></a>Utilisation des ressources dans votre implémentation de DLL

Comme indiqué ci-dessus, le chargement de ressources par défaut parcourt la liste des `CDynLinkLibrary` objets qui recherchent le premier fichier exe ou dll qui a la ressource demandée. Toutes les API MFC, ainsi que l’ensemble du code interne `AfxFindResourceHandle` , utilisent pour parcourir la liste des ressources et rechercher n’importe quelle ressource, quel que soit l’endroit où elle peut résider.

Si vous souhaitez uniquement charger des ressources à partir d’un emplacement spécifique, utilisez les API `AfxGetResourceHandle` et `AfxSetResourceHandle` pour enregistrer l’ancien descripteur et définir le nouveau descripteur. Veillez à restaurer l’ancien handle de ressource avant de revenir à l’application cliente. L’exemple de TESTDLL2 utilise cette approche pour le chargement explicite d’un menu.

Le parcours de la liste présente des inconvénients qu’elle est légèrement plus lente et requiert la gestion des plages d’ID de ressource. Il présente l’avantage qu’une application cliente liée à plusieurs DLL d’extension MFC peut utiliser n’importe quelle ressource fournie par la DLL sans devoir spécifier le descripteur d’instance de DLL. `AfxFindResourceHandle`API utilisée pour parcourir la liste des ressources afin de rechercher une correspondance donnée. Elle prend le nom et le type d’une ressource et retourne le descripteur de ressource où elle a été trouvée pour la première fois (ou NULL).

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Écriture d’une application qui utilise la version de la DLL

### <a name="application-requirements"></a>Configuration requise pour l’application

Une application qui utilise la version partagée de MFC doit suivre quelques règles simples :

- Il doit avoir un `CWinApp` objet et suivre les règles standard pour une pompe de messages.

- Elle doit être compilée avec un ensemble d’indicateurs de compilateur requis (voir ci-dessous).

- Elle doit être liée aux bibliothèques d’importation MFCxx. En définissant les indicateurs requis du compilateur, les en-têtes MFC déterminent au moment de la liaison la bibliothèque avec laquelle l’application doit établir une liaison.

- Pour exécuter le fichier exécutable, MFCxx.DLL doit se trouver sur le chemin d’accès ou dans le répertoire système de Windows.

### <a name="building-with-the-development-environment"></a>Création avec l’environnement de développement

Si vous utilisez le Makefile interne avec la plupart des valeurs par défaut standard, vous pouvez facilement modifier le projet pour générer la version de la DLL.

L’étape suivante suppose que vous disposez d’une application MFC correctement opérationnelle liée à NAFXCWD. LIB (pour déboguer) et NAFXCW. LIB (pour la version commerciale) et vous souhaitez la convertir pour utiliser la version partagée de la bibliothèque MFC. Vous exécutez l’environnement de Visual C++ et disposez d’un fichier de projet interne.

1. Dans le menu **projets** , cliquez sur **Propriétés**. Dans la page **général** , sous **paramètres par défaut du projet**, définissez Microsoft Foundation classes pour **utiliser MFC dans une DLL partagée** (MFCxx (d). dll).

### <a name="building-with-nmake"></a>Génération avec NMAKE

Si vous utilisez la fonctionnalité de Makefile externe de l’Visual C++ ou si vous utilisez NMAKE directement, vous devrez modifier votre makefile pour prendre en charge les options du compilateur et de l’éditeur de liens.

Indicateurs requis du compilateur :

- **/D_AFXDLL/MD** 
   **/D_AFXDLL**

Les en-têtes MFC standard nécessitent la définition de ce symbole :

- **/MD** L’application doit utiliser la version DLL de la bibliothèque Runtime C

Tous les autres indicateurs de compilateur suivent les valeurs par défaut MFC (par exemple, _DEBUG pour le débogage).

Modifiez la liste des bibliothèques de l’éditeur de liens. Modifiez NAFXCWD. LIB vers MFCxxD. LIB et change NAFXCW. LIB vers MFCxx. LIB. Remplacez LIBC. LIB avec MSVCRT. LIB. Comme pour toute autre bibliothèque MFC, il est important de placer MFCxxD. LIB **avant** les bibliothèques C Runtime.

Ajoutez **ou D_AFXDLL** éventuellement à vos options de compilateur de ressources de vente au détail et de débogage (celui qui compile réellement les ressources avec **/r**). Cela rend votre exécutable final plus petit en partageant les ressources qui sont présentes dans les DLL MFC.

Une régénération complète est nécessaire une fois que ces modifications ont été effectuées.

### <a name="building-the-samples"></a>Génération des exemples

La plupart des exemples de programmes MFC peuvent être générés à partir d’Visual C++ ou d’un MAKEFILE partagé basé sur NMAKE à partir de la ligne de commande.

Pour convertir l’un de ces exemples afin d’utiliser MFCxx.DLL, vous pouvez charger le. Fichier MAK dans le Visual C++ et définissez les options du projet comme décrit ci-dessus. Si vous utilisez la build NMAKE, vous pouvez spécifier « AFXDLL = 1 » sur la ligne de commande NMAKE et générer l’exemple à l’aide des bibliothèques MFC partagées.

L’exemple de concepts avancés MFC [DLLHUSK](../overview/visual-cpp-samples.md) est généré avec la version DLL de MFC. Cet exemple illustre non seulement comment créer une application liée à MFCxx.DLL, mais il illustre également d’autres fonctionnalités de l’option d’empaquetage de DLL MFC telles que les dll d’extension MFC décrites plus loin dans cette note technique.

### <a name="packaging-notes"></a>Notes de Packaging

Version commerciale des dll (MFCxx [U]. DLL) sont librement redistribuables. La version de débogage des dll n’est pas redistribuable librement et doit être utilisée uniquement pendant le développement de votre application.

Les dll de débogage sont fournies avec des informations de débogage. En utilisant le débogueur Visual C++, vous pouvez suivre l’exécution de votre application ainsi que de la DLL. Les dll de mise en version (MFCxx [U]. DLL) ne contiennent pas d’informations de débogage.

Si vous personnalisez ou régénérez les dll, vous devez les appeler autre chose que « MFCxx » dans le fichier SRC MFC MFCDLL. MAK décrit les options de génération et contient la logique de changement de nom de la DLL. Le changement de nom des fichiers est nécessaire, car ces dll sont potentiellement partagées par de nombreuses applications MFC. Le fait de faire en sorte que votre version personnalisée des DLL MFC remplace celles installées sur le système peut bloquer une autre application MFC à l’aide des DLL MFC partagées.

La reconstruction des DLL MFC n’est pas recommandée.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Comment l' MFCxx.DLL est implémentée

La section suivante décrit comment la DLL MFC (MFCxx.DLL et MFCxxD.DLL) est implémentée. La compréhension des détails ici n’est pas non plus importante si vous voulez utiliser la DLL MFC avec votre application. Les détails ne sont pas essentiels pour comprendre comment écrire une DLL d’extension MFC, mais la compréhension de cette implémentation peut vous aider à écrire votre propre DLL.

### <a name="implementation-overview"></a>Vue d’ensemble de l’implémentation

La DLL MFC est en réalité un cas spécial d’une DLL d’extension MFC, comme décrit ci-dessus. Il a un très grand nombre d’exportations pour un grand nombre de classes. Nous faisons quelques opérations supplémentaires dans la DLL MFC qui la rendent encore plus spéciale qu’une DLL d’extension MFC standard.

### <a name="win32-does-most-of-the-work"></a>Win32 effectue la majeure partie du travail

La version 16 bits de MFC nécessitait un certain nombre de techniques spéciales, notamment les données par application sur le segment de pile, les segments spéciaux créés par un code assembleur 80x86, les contextes d’exception par processus et d’autres techniques. Win32 prend directement en charge les données par processus dans une DLL, ce que vous souhaitez la plupart du temps. Pour la plupart des MFCxx.DLL est simplement NAFXCW. LIB empaqueté dans une DLL. Si vous examinez le code source MFC, vous trouverez très peu #ifdef _AFXDLL, car il y a très peu de cas spéciaux qui doivent être faits. Les cas spéciaux qui sont spécifiques à la gestion de Win32 sur Windows 3,1 (également connu sous le nom de Win32s). Win32s ne prend pas en charge les données de DLL par processus directement, de sorte que la DLL MFC doit utiliser les API de stockage local des threads (TLS) Win32 pour obtenir les données locales du processus.

### <a name="impact-on-library-sources-additional-files"></a>Impact sur les sources de bibliothèque, fichiers supplémentaires

L’impact de la version de **_AFXDLL** sur les sources et en-têtes de la bibliothèque de classes MFC normale est relativement mineur. Il existe un fichier de version spéciale (AFXV_DLL. H), ainsi qu’un fichier d’en-tête supplémentaire (AFXDLL_. H) inclus dans le AFXWIN principal. En-tête H. AFXDLL_. L’en-tête H comprend la `CDynLinkLibrary` classe et d’autres détails d’implémentation des `_AFXDLL` applications et des dll d’extension MFC. AFXDLLX. L’en-tête H est fourni pour générer des dll d’extension MFC (voir ci-dessus pour plus d’informations).

Les sources standard de la bibliothèque MFC dans la source de code MFC contiennent du code conditionnel supplémentaire sous le `_AFXDLL` #ifdef. Un fichier source supplémentaire (DLLINIT. CPP) contient le code d’initialisation de la DLL supplémentaire et un autre Glue pour la version partagée de MFC.

Pour générer la version partagée de MFC, des fichiers supplémentaires sont fournis. (Voir ci-dessous pour plus d’informations sur la génération de la DLL.)

- Directionnelle. Les fichiers DEF sont utilisés pour exporter les points d’entrée de DLL MFC pour les versions Debug (MFCxxD. DEF) et Release (MFCxx. DEF) de la DLL.

- Pièce. Fichier RC (MFCDLL. RC) contient toutes les ressources MFC standard et une ressource VERSIONINFO pour la DLL.

- Un. Fichier CLW (MFCDLL. CLW) est fourni pour permettre l’exploration des classes MFC à l’aide de ClassWizard. Remarque : cette fonctionnalité n’est pas spécifique à la version DLL de MFC.

### <a name="memory-management"></a>Gestion de la mémoire

Une application utilisant MFCxx.DLL utilise un allocateur de mémoire commun fourni par MSVCRTxx.DLL, la DLL du runtime C partagé. L’application, toutes les dll d’extension MFC, ainsi que les DLL MFC elles-mêmes utilisent cet allocateur de mémoire partagée. En utilisant une DLL partagée pour l’allocation de mémoire, les DLL MFC peuvent allouer de la mémoire qui est libérée par la suite par l’application ou vice versa. Étant donné que l’application et la DLL doivent utiliser le même allocateur, vous ne devez pas remplacer l’opérateur global C++ **New** ou l' **opérateur delete**. Les mêmes règles s’appliquent au reste des routines d’allocation de mémoire Runtime C (telles que **malloc**, **realloc**, **Free**et autres).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Ordinaux et classe __declspec (dllexport) et nom de la DLL

Nous n’utilisons pas les `class` **`__declspec(dllexport)`** fonctionnalités du compilateur C++. Au lieu de cela, une liste d’exportations est incluse avec les sources de la bibliothèque de classes (MFCxx. DEF et MFCxxD. DEF). Seul l’ensemble sélectionné de points d’entrée (fonctions et données) est exporté. D’autres symboles, tels que les classes ou les fonctions d’implémentation privée MFC, ne sont pas exportés. toutes les exportations sont effectuées par ordinal sans nom de chaîne dans la table de noms résidents ou non résidents.

L’utilisation de `class` **`__declspec(dllexport)`** peut être une alternative viable pour la génération de dll plus petites, mais dans le cas d’une dll volumineuse comme MFC, le mécanisme d’exportation par défaut a des limites d’efficacité et de capacité.

Cela signifie que nous pouvons empaqueter une grande quantité de fonctionnalités dans la MFCxx.DLL de mise en production qui est uniquement d’environ 800 Ko sans compromettre beaucoup d’exécution ou de vitesse de chargement. MFCxx.DLL aurait été de 100 000 fois cette technique n’a pas été utilisée. Cela permet également d’ajouter des points d’entrée supplémentaires à la fin de. Fichier DEF pour permettre un contrôle de version simple sans compromettre la vitesse et l’efficacité de la taille de l’exportation par ordinal. Les révisions majeures de la version de la bibliothèque de classes MFC modifient le nom de la bibliothèque. Autrement dit, MFC30.DLL est la DLL redistribuable contenant la version 3,0 de la bibliothèque de classes MFC. Une mise à niveau de cette DLL, par exemple, dans une hypothétique MFC 3,1, la DLL serait nommée MFC31.DLL à la place. Là encore, si vous modifiez le code source MFC pour produire une version personnalisée de la DLL MFC, utilisez un nom différent (et de préférence un sans « MFC » dans le nom).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
