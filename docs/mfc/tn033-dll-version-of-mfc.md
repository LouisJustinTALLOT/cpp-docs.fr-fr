---
title: 'TN033 : version DLL de MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.dll
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: 89a9fddd6f12f92d18bcd6fc75f117beb14746f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571819"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033 : version DLL de MFC

Cette note décrit comment vous pouvez utiliser la MFCxx.DLL et MFCxxD.DLL (où x est le numéro de version MFC) partagé des bibliothèques de liens dynamiques avec les applications MFC et les DLL d’extension MFC. Pour plus d’informations sur les DLL MFC normales, consultez [à l’aide de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Cette note technique couvre trois aspects de la DLL. Les deux derniers sont pour les utilisateurs plus avancés :

- [Façon dont vous générez une DLL d’Extension MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Façon dont vous générez une application MFC qui utilise la version DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Comment la bibliothèque MFC partagée des bibliothèques de liens dynamiques sont implémentées.](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Si vous êtes intéressé de la génération d’une DLL à l’aide de MFC qui peut être utilisé avec les applications non-MFC (on parle une DLL MFC normale), reportez-vous à [Note technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Vue d’ensemble de la prise en charge MFCxx.DLL : la terminologie et les fichiers

**DLL MFC normale**: une DLL MFC normale vous permet de générer une DLL autonome à l’aide de certaines des classes MFC. Interfaces au-delà de la limite DLL / l’application sont des interfaces de « C », et l’application cliente ne devra pas être une application MFC.

Il s’agit de la version de prise en charge DLL pris en charge dans MFC 1.0. Il est décrit dans [Note technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) et l’exemple de Concepts avancés MFC [DLLScreenCap](../visual-cpp-samples.md).

> [!NOTE]
> À compter de Visual C++ version 4.0, le terme **USRDLL** est obsolète et a été remplacé par une DLL MFC normale liée de manière statique aux MFC. Vous pouvez également mettre une DLL MFC qui lie dynamiquement à MFC standard.

MFC 3.0 (et versions ultérieures) prend en charge des DLL MFC normales avec de nouvelles fonctionnalités, notamment les classes OLE et de la base de données.

**AFXDLL**: cela est également appelé à la version partagée des bibliothèques MFC. Il s’agit de la nouvelle prise en charge DLL ajoutée dans MFC 2.0. La bibliothèque MFC elle-même est dans un nombre de DLL (décrits ci-dessous) et une application cliente ou une DLL liée de manière dynamique les DLL dont il a besoin. Interfaces au-delà de la limite DLL d’application sont C + c++ / interfaces de classes de MFC. L’application cliente doit être une application MFC. Cela prend en charge toutes les fonctionnalités de MFC 3.0 (exception : UNICODE n’est pas pris en charge pour les classes de base de données).

> [!NOTE]
> À compter de Visual C++ version 4.0, ce type de DLL est appelé pour une « DLL d’Extension. »

Cette note utilisera MFCxx.DLL pour faire référence à l’ensemble du jeu de DLL MFC, qui inclut :

- Débogage : MFCxxD.DLL (combiné) et MFCSxxD.LIB (statique).

- Version : MFCxx.DLL (combiné) et MFCSxx.LIB (statique).

- Débogage d’Unicode : MFCxxUD.DLL (combiné) et MFCSxxD.LIB (statique).

- Version d’Unicode : MFCxxU.DLL (combiné) et MFCSxxU.LIB (statique).

> [!NOTE]
> Le MFCSxx [U] [D]. Lib sont utilisées en conjonction avec la bibliothèque MFC des DLL partagées. Ces bibliothèques contiennent du code qui doit être liée de manière statique à l’application ou la DLL.

Une application des liens vers les bibliothèques d’importation correspondante :

- Déboguer : MFCxxD.LIB

- Mise en production : MFCxx.LIB

- Débogage d’Unicode : MFCxxUD.LIB

- Version d’Unicode : MFCxxU.LIB

Une « DLL d’Extension MFC » est une DLL basée sur MFCxx.DLL (et/ou l’autres MFC des DLL partagées). Ici l’architecture des composants MFC intervient. Si vous dérivez une classe utile à partir d’une classe MFC, ou créez un autre type MFC toolkit, vous pouvez le placer dans une DLL. Que les DLL utilise MFCxx.DLL, comme l’application cliente ultimate. Ainsi, les classes terminales réutilisables, classes de base réutilisables et classes de document/vue réutilisables.

## <a name="pros-and-cons"></a>Avantages et inconvénients

Pourquoi devez-vous utiliser la version partagée des MFC

- À l’aide de la bibliothèque partagée peut entraîner des applications plus petites (une application minimale qui consomme l’essentiel de la bibliothèque MFC est inférieure à 10 Ko).

- La version partagée des MFC prend en charge les DLL d’Extension MFC et DLL MFC normales.

- Création d’une application qui utilise les bibliothèques MFC partagées est plus rapide que la création d’une application MFC liée statiquement, car il n’est pas nécessaire de lier l’application MFC elle-même. Cela est particulièrement vrai dans **déboguer** builds où l’éditeur de liens doit compacter les informations de débogage, en les liant avec une DLL qui contient déjà les informations de débogage, il est moins les informations de débogage à compacter dans votre application.

Pourquoi vous pas utilisez la version partagée des MFC :

- Copie d’une application qui utilise la bibliothèque partagée nécessite que vous expédiez MFCxx.DLL (et autres) bibliothèque avec votre programme. MFCxx.DLL peut être redistribué, comme de nombreuses DLL, mais vous devez toujours installer la DLL dans votre programme d’installation. En outre, vous devez expédier MSVCRTxx.DLL, qui contient la bibliothèque runtime C qui est utilisée par votre programme et les DLL MFC elles-mêmes.

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Comment écrire une DLL d’Extension MFC

Une DLL d’Extension MFC est une DLL qui contient les classes et fonctions écrites pour améliorer les fonctionnalités des classes MFC. Une DLL d’Extension MFC utilise les DLL MFC partagée de la même façon qu’une application utilise, avec quelques considérations supplémentaires :

- Le processus de génération est similaire à la création d’une application qui utilise les bibliothèques MFC partagées avec quelques autres options du compilateur et éditeur de liens.

- Une DLL d’Extension MFC n’a pas un `CWinApp`-classe dérivée.

- Une DLL d’Extension MFC doit fournir un spécial `DllMain`. AppWizard fournit un `DllMain` fonction que vous pouvez modifier.

- Une DLL d’Extension MFC fournit généralement une routine d’initialisation pour créer un `CDynLinkLibrary` si l’extension MFC DLL souhaite exporter `CRuntimeClass`es ou ressources à l’application. Une classe dérivée de `CDynLinkLibrary` peut être utilisé si les données de chaque application doivent être gérées par la DLL d’extension MFC.

Ces considérations sont décrits plus en détail ci-dessous. Vous devez également vous reporter à l’exemple de Concepts avancés MFC [DLLHUSK](../visual-cpp-samples.md) dans la mesure où il illustre :

- Création d’une application en utilisant les bibliothèques partagées. (DLLHUSK. EXE est une application MFC qui lie dynamiquement aux bibliothèques MFC, ainsi que d’autres DLL).

- Création d’une DLL d’Extension MFC. (Notez les indicateurs spéciaux tels que `_AFXEXT` qui sont utilisés dans la création d’une DLL d’extension MFC)

- Deux exemples de DLL d’Extension MFC. Un montre la structure de base d’une DLL d’Extension MFC avec des exportations limitées (TESTDLL1) et d’autres le montre l’exportation d’une interface de classe entière (TESTDLL2).

L’application cliente et les DLL d’extension MFC doivent utiliser la même version de MFCxx.DLL. Vous devez suivre la convention de DLL MFC et fournir les deux un débogage et la vente au détail (/ release) version de votre DLL d’extension MFC. Cela permet à des programmes de client pour générer les versions debug et vente au détail de leurs applications et de les lier avec le débogage approprié ou une version commerciale de toutes les DLL.

> [!NOTE]
>  Étant donné que C++ problèmes d’exportation et nommez l’altération, la liste d’exportation à partir d’une DLL d’extension MFC peut-être différer entre les versions de débogage et de la vente au détail de la même DLL et les DLL pour différentes plateformes. La vente au détail MFCxx.DLL a environ 2000 exporté des points d’entrée ; le débogage MFCxxD.DLL a environ 3000 points d’entrée exportés.

### <a name="quick-note-on-memory-management"></a>Note rapide sur la gestion de la mémoire

La section intitulée « Gestion de la mémoire, » vers la fin de cette note technique, décrit l’implémentation de MFCxx.DLL avec la version partagée des MFC. Les informations que vous devez savoir pour implémenter simplement une extension MFC que DLL est décrite ici.

MFCxx.DLL et toutes les DLL d’extension MFC chargés dans l’espace d’adressage d’une application cliente utiliseront l’allocateur de mémoire de même, le chargement des ressources et autres États « globales » MFC comme s’ils étaient dans la même application. C’est important, car les bibliothèques de DLL non - MFC et les DLL MFC normales liées de manière statique aux MFC l’inverse exact et que chaque DLL affecte en dehors de son propre pool de mémoire.

Si une DLL d’extension MFC alloue de la mémoire, cette mémoire peut alors être librement mélangée avec tout autre objet alloué par l’application. En outre, si une application qui utilise les bibliothèques MFC partagées tombe en panne, la protection du système d’exploitation maintenir l’intégrité de toute autre application MFC partageant la DLL.

De même les autres États « globales » de MFC, telles que le fichier exécutable en cours pour charger les ressources à partir, sont également partagés entre l’application cliente et toutes les DLL d’extension MFC ainsi MFCxx.DLL lui-même.

### <a name="building-an-mfc-extension-dll"></a>Création d’une DLL d’extension MFC

Vous pouvez utiliser AppWizard pour créer un projet DLL d’extension MFC, et il génère automatiquement les paramètres de l’éditeur de liens et le compilateur approprié. Il a été également générer un `DllMain` fonction que vous pouvez modifier.

Si vous convertissez un projet existant à une DLL d’extension MFC, commencez par les règles standard pour la création d’une application à l’aide de la version partagée des MFC, puis procédez comme suit :

- Ajouter **/D_AFXEXT** pour les indicateurs de compilateur. Dans la boîte de dialogue Propriétés du projet, sélectionnez le nœud C/C++. Puis sélectionnez la catégorie de préprocesseur. Ajouter `_AFXEXT` au champ définir des Macros, séparant chacun des éléments par des points-virgules.

- Supprimer le **/Gy** commutateur de compilateur. Dans la boîte de dialogue Propriétés du projet, sélectionnez le nœud C/C++. Puis sélectionnez la catégorie de la génération de Code. Assurez-vous que l’option « Activer la liaison au niveau des fonctions » n’est pas activée. Cela rend plus facile exporter des classes, car l’éditeur de liens ne supprime pas les fonctions non référencées. Si le projet d’origine est utilisé pour générer une expression régulière MFC DLL liées de manière statique aux MFC, la modification la **/MT [d]** l’option du compilateur **/MD [d]**.

- Générer une bibliothèque d’exportation avec le **/DLL** option au lien. Il sera configuré lorsque vous créez une nouvelle cible, en spécifiant la bibliothèque de liens dynamiques Win32 en tant que le type cible.

### <a name="changing-your-header-files"></a>Modification de vos fichiers d’en-tête

L’objectif d’une DLL d’extension MFC consiste généralement à exporter des fonctionnalités communes pour une ou plusieurs applications qui peuvent utiliser cette fonctionnalité. Cela se résume à l’exportation des classes et fonctions globales qui sont disponibles pour vos applications clientes.

Pour ce faire, vous devez vous assurer que chacune de ces fonctions de membre est marqué comme importer ou exporter comme il convient. Cela nécessite de déclarations spéciale : `__declspec(dllexport)` et `__declspec(dllimport)`. Lorsque vos classes sont utilisées par les applications clientes, vous le souhaitez être déclarées comme `__declspec(dllimport)`. Lorsque la DLL d’extension MFC est en cours de génération, ils doivent être déclarés en tant que `__declspec(dllexport)`. En outre, les fonctions doivent être réellement exportées, afin que les programmes clients procéder à une liaison au moment du chargement.

Pour exporter votre classe entière, utilisez `AFX_EXT_CLASS` dans la définition de classe. Cette macro est définie par l’infrastructure en tant que `__declspec(dllexport)` lorsque `_AFXDLL` et `_AFXEXT` est défini, mais est définie comme `__declspec(dllimport)` lorsque `_AFXEXT` n’est pas défini. `_AFXEXT` comme décrit ci-dessus, est définie uniquement lors de la création de votre DLL d’extension MFC. Exemple :

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>N’exportez ne pas la classe entière

Vous pouvez être amené à exporter seulement nécessaires membres individuels de votre classe. Par exemple, si vous exportez un `CDialog`-classe dérivée, vous devrez peut-être uniquement exporter le constructeur et le `DoModal` appeler. Vous pouvez exporter ces membres à l’aide de la DLL. Fichier DEF, mais vous pouvez également utiliser `AFX_EXT_CLASS` dans la même façon sur les membres individuels, vous devez exporter.

Exemple :

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

Lorsque vous effectuez cette opération, vous pouvez exécuter dans un autre problème, car vous n’exportez plus tous les membres de la classe. Le problème réside dans le fonctionnement des macros MFC. En fait, plusieurs macros d’assistance MFC déclarent ou définissent des membres de données. Par conséquent, ces membres de données devez également être exportées à partir de votre DLL.

Par exemple, la macro DECLARE_DYNAMIC est définie comme suit lors de la création d’une DLL d’extension MFC :

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \

```

La ligne qui commence » statique `AFX_DATA`» déclare un objet statique à l’intérieur de votre classe. Pour exporter cette classe correctement et accéder aux informations de runtime à partir d’un client. EXE, vous devez exporter cet objet statique. Car l’objet statique est déclaré avec le modificateur `AFX_DATA`, vous devez uniquement définir `AFX_DATA` être `__declspec(dllexport)` lors de la création de votre DLL, puis attribuez-le comme `__declspec(dllimport)` lors de la création de votre fichier exécutable du client.

Comme indiqué ci-dessus, `AFX_EXT_CLASS` est déjà définie de cette façon. Vous devez simplement ré-définir `AFX_DATA` pour être le même que `AFX_EXT_CLASS` autour de votre définition de classe.

Exemple :

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

MFC utilise toujours le `AFX_DATA` symbole sur des éléments de données qu’il définit dans ses macros, donc cette technique fonctionne pour tous ces scénarios. Par exemple, il fonctionnera pour DECLARE_MESSAGE_MAP.

> [!NOTE]
> Si vous exportez la classe entière plutôt que les membres sélectionnés de la classe, les données membres statiques sont automatiquement exportées.

Vous pouvez utiliser la même technique pour exporter automatiquement la `CArchive` opérateur d’extraction pour les classes qui utilisent les macros DECLARE_SERIAL et IMPLEMENT_SERIAL. Exporter l’opérateur de l’archive en délimitant les déclarations de classe (situé dans le. Fichier de H) par le code suivant :

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>Limitations de _AFXEXT

Vous pouvez utiliser le _**AFXEXT** symbole du préprocesseur pour votre extension MFC DLL tant que vous n’avez pas plusieurs couches de DLL d’extension MFC. Si vous disposez d’extension MFC DLL qui appellent ou dérivent des classes dans vos propres MFC DLL d’extension, qui ensuite dériver des classes MFC, vous devez utiliser votre propre symbole de préprocesseur pour éviter toute ambiguïté.

Le problème est que dans Win32, vous devez déclarer explicitement toutes les données en tant que `__declspec(dllexport)` s’il doit être exporté à partir d’une DLL, et `__declspec(dllimport)` s’il doit être importé à partir d’une DLL. Lorsque vous définissez `_AFXEXT`, les en-têtes MFC Assurez-vous que `AFX_EXT_CLASS` est défini correctement.

Lorsque vous avez plusieurs couches, un symbole comme `AFX_EXT_CLASS` n’est pas suffisant, dans la mesure où une DLL d’extension MFC peut exporter de nouvelles classes, ainsi que l’importation d’autres classes à partir d’une autre DLL d’extension MFC. Pour résoudre ce problème, utilisez un symbole de préprocesseur spécial qui indique que vous générez la DLL mais plutôt à l’aide de la DLL. Par exemple, imaginez deux DLL d’extension MFC, A.DLL et B.DLL. Chaque exportent certaines classes dans A.H et B.H, respectivement. B.DLL utilise les classes de A.DLL. Les fichiers d’en-tête ressemblent à ceci :

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

Lorsque A.DLL est générée, il est créé avec **/DA_IMPL** et lorsque B.DLL est générée, il est créé avec **/DB_IMPL**. En utilisant des symboles distincts pour chaque DLL, CExampleB est exporté et CExampleA est importé lors de la génération de B.DLL. CExampleA est exporté lors de la génération de A.DLL et importé lorsqu’il est utilisé par B.DLL (ou un autre client).

Ce type de superposition ne peut pas être effectué lors de l’utilisation intégrée `AFX_EXT_CLASS` et `_AFXEXT` les symboles du préprocesseur. La technique décrite ci-dessus résout ce problème de manière à la différence pas que le mécanisme d’application MFC elle-même utilise lors de la création de ses DLL d’extension OLE, base de données et réseau MFC.

### <a name="not-exporting-the-entire-class"></a>N’exportez ne pas la classe entière

Là encore, vous devez faire particulièrement attention lorsque vous n’exportez pas une classe entière. Vous devez vous assurer que les éléments de données nécessaires créés par les macros MFC sont exportés correctement. Cela est possible en ré-définissant `AFX_DATA` à la macro de votre classe spécifique. Cela doit être effectuée à tout moment que vous n’exportez pas la classe entière.

Exemple :

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

Voici le code exact que vous devez placer dans votre fichier source principal pour votre DLL d’extension MFC. Il doit venir après que la norme inclut. Notez que lorsque vous utilisez AppWizard pour créer des fichiers de démarrage d’une DLL d’extension MFC, il fournit un `DllMain` pour vous.

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

L’appel à `AfxInitExtensionModule` capture les classes de runtime de modules (`CRuntimeClass` structures), ainsi que ses fabriques d’objets (`COleObjectFactory` objets) pour une utilisation ultérieurement, lorsque le `CDynLinkLibrary` objet est créé. L’appel (facultatif) à `AfxTermExtensionModule` permet de MFC nettoyer la DLL d’extension MFC lorsque chaque processus détache (ce qui se produit lorsque le processus se termine, ou lorsque la DLL est déchargée à la suite d’un `FreeLibrary` appeler) à partir de la DLL d’extension MFC. Depuis la plupart des DLL ne sont pas chargées dynamiquement d’extension MFC (en règle générale, elles sont liées par le biais de leurs bibliothèques d’importation), l’appel à `AfxTermExtensionModule` n’est généralement pas nécessaire.

Si votre application charge et libère dynamiquement les DLL d’extension MFC, veillez à appeler `AfxTermExtensionModule` comme indiqué ci-dessus. Veillez également à utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions Win32 `LoadLibrary` et `FreeLibrary`) si votre application utilise plusieurs threads ou s’il charge dynamiquement une DLL d’extension MFC. À l’aide de `AfxLoadLibrary` et `AfxFreeLibrary` garantit que le code de démarrage et d’arrêt qui s’exécute lorsque la DLL d’extension MFC est chargé et déchargé n’altère pas l’état global de MFC.

Le fichier d’en-tête AFXDLLX. H contient des définitions spéciales pour les structures utilisées dans les DLL d’extension MFC, telles que la définition de `AFX_EXTENSION_MODULE` et `CDynLinkLibrary`.

Global *extensionDLL* doit être déclarée comme indiqué. Contrairement à la version 16 bits de MFC, vous pouvez allouer de la mémoire et appeler des fonctions MFC pendant ce temps, dans la mesure où la MFCxx.DLL est entièrement initialisé au moment où votre `DllMain` est appelée.

### <a name="sharing-resources-and-classes"></a>Partage des ressources et des Classes

DLL d’extension MFC simples doivent exporter uniquement quelques fonctions de faible bande passante à l’application cliente et rien de plus. Vous souhaiterez plus DLL intensif de l’interface utilisateur exporter des ressources et des classes C++ à l’application cliente.

Exportation de ressources s’effectue via une liste de ressources. Dans chaque application est une liste liée unique de `CDynLinkLibrary` objets. Lorsque vous recherchez une ressource, la plupart des implémentations MFC standard qui chargent des ressources commencez par consulter le module de ressources en cours (`AfxGetResourceHandle`) et s’il n'existe pas de parcours de la liste des `CDynLinkLibrary` objets tentant de charger la ressource demandée.

La création dynamique d’objets C++ étant donné un nom de classe C++ est similaire. Le mécanisme de la désérialisation d’objets MFC doit avoir tous les `CRuntimeClass` objets enregistrés afin qu’il puisse reconstruire en créant dynamiquement des objets C++ du type requis en fonction de ce qui était stocké précédemment.

Si vous souhaitez que l’application cliente pour utiliser des classes dans votre DLL d’extension MFC qui sont `DECLARE_SERIAL`, vous devez exporter vos classes pour être visible à l’application cliente. Cela est également effectuée en parcourant le `CDynLinkLibrary` liste.

Dans le cas de l’exemple de Concepts avancés MFC [DLLHUSK](../visual-cpp-samples.md), la liste ressemble à ceci :

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

MFCxx.DLL est généralement la dernière sur la ressource et la liste de classe. MFCxx.DLL inclut toutes les ressources MFC standards, y compris les chaînes d’invite pour tous les ID de commande standard. En le plaçant à la fin de la liste permet de DLL et l’application du client pour ne pas avoir une sa propre copie des ressources MFC standards, mais au s’appuient sur les ressources partagées dans la MFCxx.DLL à la place.

Fusionner les ressources et les noms de classes de toutes les DLL dans l’espace de noms de l’application cliente a l’inconvénient : vous devez être prudent quels sont les ID ou les noms que vous sélectionnez. Vous pouvez bien sûr désactiver cette fonctionnalité en soit ne pas d’exportation vos ressources ou un `CDynLinkLibrary` objet à l’application cliente. Le [DLLHUSK](../visual-cpp-samples.md) exemple gère l’espace de noms de ressource partagée à l’aide de plusieurs fichiers d’en-tête. Consultez [Note technique 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) pour d’autres conseils sur l’utilisation de fichiers de ressources partagées.

### <a name="initializing-the-dll"></a>L’initialisation de la DLL

Comme mentionné ci-dessus, vous souhaiterez généralement créer un `CDynLinkLibrary` objet afin d’exporter vos ressources et les classes à l’application cliente. Vous devez fournir un point d’entrée exporté pour initialiser la DLL. Au minimum, il s’agit d’une routine de void qui n’accepte aucun argument et ne retourne rien, mais il peut être comme vous le souhaitez.

Chaque application de client qui souhaite utiliser votre DLL doit appeler cette routine d’initialisation, si vous utilisez cette approche. Vous pouvez également allouer cela `CDynLinkLibrary` de l’objet dans votre `DllMain` juste après l’appel `AfxInitExtensionModule`.

La routine d’initialisation doit créer un `CDynLinkLibrary` objet dans le segment de mémoire de l’application active, associée à vos informations de la DLL d’extension MFC. Cela est possible avec les éléments suivants :

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Le nom de la routine, *InitXxxDLL* dans cet exemple, peut être comme vous le souhaitez. Il n’a pas besoin être **extern « C »**, mais ceci met plus facile à gérer la liste d’exportation.

> [!NOTE]
> Si vous utilisez votre DLL d’extension MFC à partir d’une DLL MFC normale, vous devez exporter cette fonction d’initialisation. Cette fonction doit être appelée à partir de la DLL MFC standard avant d’utiliser les classes DLL d’extension MFC ou les ressources.

### <a name="exporting-entries"></a>Exportation des entrées

Le simple pour exporter vos classes consiste à utiliser `__declspec(dllimport)` et `__declspec(dllexport)` sur chaque classe et de la fonction globale que vous souhaitez exporter. Cela rend beaucoup plus facile, mais est moins efficace que d’affectation de noms chaque point d’entrée (décrit ci-dessous) dans la mesure où vous avez moins de contrôle sur ce que les fonctions sont exportées et vous ne pouvez pas exporter les fonctions par ordinal. TESTDLL1 et TESTDLL2 utilisent cette méthode pour exporter leurs entrées.

Une méthode plus efficace (et la méthode utilisée par MFCxx.DLL) consiste à exporter chaque entrée manuellement en le nommant chaque entrée dans le. Fichier DEF. Étant donné que nous avons exportation sélectives exportations à partir de notre DLL (autrement dit, pas tous les éléments), nous devons déterminer les interfaces particuliers, nous souhaitons exporter. C’est difficile, car vous devez spécifier les noms tronqués à l’éditeur de liens sous la forme d’entrées dans le. Fichier DEF. N’exportons pas toutes les classes C++, sauf si vous devez vraiment avoir un lien symbolique pour qu’il.

Si vous avez tenté d’exportation C++ classes avec un. Avant, vous pouvez souhaiter de développer un outil pour générer automatiquement de cette liste de fichiers DEF. Cela est possible à l’aide d’un processus de liaison de deux étapes. Lier la DLL qu’une seule fois avec aucune exportation, et autoriser l’éditeur de liens générer un. Fichier de mappage. La barre d’outils. Fichier de mappage peut être utilisé pour générer une liste des fonctions qui doivent être exportés, donc avec certains réorganisation, il peut être utilisé pour générer vos entrées d’exportation pour votre. Fichier DEF. La liste d’exportation pour MFCxx.DLL et OLE et DLL d’extension MFC de base de données, plusieurs milliers de nombre, a été générée avec un tel processus (bien qu’il n’est pas entièrement automatique et requiert certains main réglage jambes dans un certain temps).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Une DLL d’Extension MFC n’a pas un `CWinApp`-objet de son propre dérivé ; au lieu de cela, il doit fonctionner avec le `CWinApp`-objet de l’application cliente dérivé. Cela signifie que l’application cliente possède la pompe de messages principale, la boucle inactive et ainsi de suite.

Si votre DLL d’Extension MFC doit gérer des données supplémentaires pour chaque application, vous pouvez dériver une nouvelle classe à partir de `CDynLinkLibrary` créez-la dans le InitXxxDLL routine Décrivez ci-dessus. Lors de l’exécution, la DLL peut consulter la liste de l’application en cours de `CDynLinkLibrary` objets pour trouver celui pour cette DLL d’extension MFC particulier.

### <a name="using-resources-in-your-dll-implementation"></a>Utilisation de ressources dans votre implémentation de DLL

Comme mentionné ci-dessus, la charge de ressources par défaut sera parcourent la liste des `CDynLinkLibrary` objets, recherchez la première EXE ou DLL dans laquelle la ressource demandée. Toutes les API de MFC, ainsi que tout le code interne utilise `AfxFindResourceHandle` pour parcourir la liste des ressources pour rechercher n’importe quelle ressource, quel que soit l’où il peut résider.

Si vous souhaitez charger uniquement les ressources à partir d’un emplacement spécifique, utilisez les API `AfxGetResourceHandle` et `AfxSetResourceHandle` pour enregistrer l’ancien handle et définir le nouveau handle. Veillez à restaurer l’ancien handle de ressource avant de retourner à l’application cliente. L’exemple TESTDLL2 utilise cette approche pour le chargement explicite d’un menu.

Parcours de la liste a les inconvénients qu’il est légèrement plus lente et nécessite la gestion de plages d’ID de ressource. Il a l’avantage qu’une application cliente qui lie à plusieurs DLL d’extension MFC pouvez utiliser n’importe quelle ressource DLL fournie sans avoir à spécifier le handle d’instance DLL. `AfxFindResourceHandle` une API utilisée pour parcourir la liste des ressources pour rechercher une correspondance donnée. Il prend le nom et le type d’une ressource et retourne le handle de ressource où il a été trouvée en premier (ou NULL).

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Écrivez une Application qui utilise la Version DLL

### <a name="application-requirements"></a>Exigences de l’application

Une application qui utilise la version partagée des MFC doit suivre quelques règles simples :

- Il doit avoir un `CWinApp` de l’objet et de respecter les règles standards pour une pompe de messages.

- Elle doit être compilée avec un jeu d’indicateurs de compilateur requis (voir ci-dessous).

- Il doit lier avec les bibliothèques d’importation MFCxx. En définissant les indicateurs de compilateur requis, les en-têtes MFC déterminent au moment de la liaison de bibliothèque dans laquelle l’application doit être liée à.

- Pour exécuter l’exécutable, MFCxx.DLL doit être sur le chemin d’accès ou dans le répertoire de système de Windows.

### <a name="building-with-the-development-environment"></a>Création de l’environnement de développement

Si vous utilisez le makefile interne avec la plupart des valeurs par défaut standards, vous pouvez facilement modifier le projet pour générer la version DLL.

L’étape suivante suppose que vous disposez d’une application MFC fonctionne correctement liée avec NAFXCWD. LIB (pour le débogage) et NAFXCW. LIB (pour la vente au détail) et que vous souhaitez convertir pour utiliser la version partagée de la bibliothèque MFC. Vous exécutez l’environnement Visual C++ et que vous disposez d’un fichier de projet interne.

1. Sur le **projets** menu, cliquez sur **propriétés**. Dans le **général** page sous **projet par défaut est**, la valeur est Microsoft Foundation Classes **utiliser les MFC dans une DLL partagée** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Génération avec NMAKE

Si vous utilisez la fonctionnalité de makefile externe de Visual C++, ou utilisez NMAKE directement, vous devrez modifier votre makefile pour prendre en charge les options du compilateur et éditeur de liens

Indicateurs de compilateur requis :

- **/ D_AFXDLL /MD**
   **/D_AFXDLL**

Les en-têtes MFC standard doivent ce symbole à définir :

- **/MD** l’application doit utiliser la version DLL de la bibliothèque Runtime C

Tous les autres indicateurs de compilateur suivent les valeurs par défaut MFC (par exemple, _DEBUG pour le débogage).

Modifier la liste de l’éditeur de liens des bibliothèques. Modification NAFXCWD. LIB à MFCxxD.LIB et modifier NAFXCW. LIB à MFCxx.LIB. Remplacez LIBC. LIB avec MSVCRT. LIB. Comme avec toute autre bibliothèque MFC, il est important que MFCxxD.LIB est placé **avant** toutes les bibliothèques runtime C.

Ajoutez éventuellement **/D_AFXDLL** aux options de compilateur de ressources à la fois votre commerciales et de débogage (celui qui compile réellement les ressources avec **/R**). Cela rend votre exécutable final plus petits en partageant les ressources qui sont présents dans les DLL MFC.

Une régénération complète est nécessaire une fois que ces modifications sont apportées.

### <a name="building-the-samples"></a>Génération des exemples

La plupart des exemples de programmes MFC peut être générée à partir de Visual C++ ou d’un MAKEFILE NMAKE compatibles partagé à partir de la ligne de commande.

Pour convertir un de ces exemples à utiliser MFCxx.DLL, vous pouvez charger le. MAK votre fichier en Visual C++ et définir les options de projet comme décrit ci-dessus. Si vous utilisez la génération NMAKE, vous pouvez spécifier « AFXDLL = 1 » sur le NMAKE ligne de commande et qui générera l’exemple en utilisant les bibliothèques MFC partagées.

L’exemple de Concepts avancés MFC [DLLHUSK](../visual-cpp-samples.md) est généré avec la version DLL de MFC. Cet exemple illustre non seulement comment créer une application liée avec MFCxx.DLL, mais il illustre également les autres fonctionnalités de l’option d’empaquetage de DLL MFC telles que des DLL d’Extension MFC décrite plus loin dans cette note technique.

### <a name="packaging-notes"></a>Notes de l’empaquetage

La version commerciale des DLL (MFCxx [U]. DLL) peuvent être redistribuées librement. La version debug des DLL ne peuvent pas être redistribuée librement et doit être utilisé uniquement pendant le développement de votre application.

La DLL de débogage sont fournis avec les informations de débogage. À l’aide du débogueur de Visual C++, vous pouvez suivre l’exécution de votre application, ainsi que la DLL. Les DLL de mise en production (MFCxx [U]. DLL) ne contiennent pas les informations de débogage.

Si vous personnalisez ou régénérez les DLL, puis vous devez appeler les quelque chose autre que le fichier de « MFCxx » The MFC SRC MFCDLL. MAK décrit les options de build et contient la logique de la modification du nom de la DLL. Renommer les fichiers est nécessaire, étant donné que ces DLL est potentiellement partagés par de nombreuses applications MFC. Avoir votre version personnalisée de l’opération de remplacement des DLL MFC, ces derniers sont installés sur le système peuvent interrompre une autre application MFC à l’aide de la DLL MFC partagée.

La reconstruction de la DLL de MFC n’est pas recommandée.

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Comment la MFCxx.DLL est implémentée

La section suivante décrit comment la DLL MFC (MFCxx.DLL et MFCxxD.DLL) est implémentée. Comprendre que les détails ici ne sont pas importantes si vous souhaitez faire sont utiliser la DLL MFC avec votre application. Les détails ici ne sont pas indispensables pour comprendre comment écrire une DLL d’extension MFC, mais la compréhension de cette implémentation peut vous aider à écrire votre propre DLL.

### <a name="implementation-overview"></a>Vue d’ensemble de l’implémentation

La DLL MFC est vraiment un cas spécial d’une DLL d’Extension MFC comme décrit ci-dessus. Il possède un très grand nombre d’exportations pour un grand nombre de classes. Il existe quelques éléments supplémentaires que nous le faisons dans la DLL MFC qui le rendent encore plus spéciaux à une DLL d’extension MFC standard.

### <a name="win32-does-most-of-the-work"></a>Win32 effectue la plupart du travail

La version 16 bits de MFC nécessaire à un nombre de techniques spéciales, y compris les données par application sur le segment de la pile, des segments spéciales créés par du code de l’assembly de 80 x 86, par processus exception contextes et d’autres techniques. Win32 prend en charge directement par traiter les données dans une DLL, qui est ce que vous souhaitez la plupart du temps. La plupart du temps MFCxx.DLL est simplement NAFXCW. LIB empaqueté dans une DLL. Si vous examinez le code source MFC, vous trouverez très peu #ifdef _AFXDLL, dans la mesure où il existe quelques cas spéciaux qui doivent être apportées. Cas spéciales qui sont requises spécifiquement pour gérer avec Win32 sur 3.1 de Windows (également appelé Win32s). Win32s ne pas les données DLL par processus prise en charge directement par conséquent, la DLL MFC doit utiliser le stockage local des threads (TLS) API Win32 pour obtenir des données locales de processus.

### <a name="impact-on-library-sources-additional-files"></a>Impact sur les Sources de la bibliothèque, des fichiers supplémentaires

L’impact de la **_AFXDLL** version sur les en-têtes et les sources de bibliothèque de classe MFC normale est relativement mineure. Il existe un fichier de version spéciale (AFXV_DLL. (H), ainsi qu’un fichier d’en-tête supplémentaires (AFXDLL_. (H) inclus par le principal AFXWIN. En-tête de H. Le AFXDLL_. En-tête de H inclut le `CDynLinkLibrary` classe et autres détails d’implémentation des deux `_AFXDLL` applications et des DLL d’Extension MFC. Le AFXDLLX. En-tête de H est fourni pour la création de DLL d’Extension MFC (voir ci-dessus pour plus d’informations).

Les sources régulières à la bibliothèque MFC dans MFC SRC ont du code conditionnel supplémentaire sous le `_AFXDLL` #ifdef. Un fichier source supplémentaire (DLLINIT. (CPP) contient le code d’initialisation de DLL supplémentaire et autres glue pour la version partagée des MFC.

Pour générer la version partagée des MFC, les fichiers supplémentaires sont fournies. (Voir ci-dessous pour plus d’informations sur la création de la DLL).

- Deux. Fichiers DEF sont utilisés pour l’exportation les points d’entrée de DLL MFC pour le débogage (MFCxxD.DEF) et (MFCxx.DEF) version finale de la DLL.

- Une barre d’outils. Fichier RC (MFCDLL. RC) contient toutes les ressources MFC standards et une ressource VERSIONINFO pour la DLL.

- A. Fichier CLW (MFCDLL. CLW) est fourni pour autoriser l’exploration de la bibliothèque MFC, classes à l’aide de ClassWizard. Remarque : cette fonctionnalité n’est pas spécifique à la version DLL de MFC.

### <a name="memory-management"></a>Gestion de la mémoire

Une application à l’aide de MFCxx.DLL utilise un allocateur de mémoire courants fourni par MSVCRTxx.DLL, la DLL de C runtime partagée. L’application, les DLL d’extension MFC et ainsi que les DLL MFC eux-mêmes utilisent cet allocateur de mémoire partagée. En utilisant une DLL partagée pour l’allocation de mémoire, les DLL MFC peuvent allouer la mémoire libérée ultérieurement par l’application, ou vice versa. Car l’application et la DLL doivent utiliser l’allocateur de même, vous ne devez pas substituer le C++ global **opérateur new** ou **opérateur delete**. Les mêmes règles s’appliquent au reste de routines d’allocation de mémoire du runtime C (tel que **malloc**, **realloc**, **gratuit**, etc.).

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Ordinaux et classe __declspec (dllexport) et les DLL d’affectation de noms

Nous n’utilisons pas la `class` **__declspec (dllexport)** fonctionnalités du compilateur C++. Au lieu de cela, une liste d’exportations est incluse dans la source de bibliothèque de classes (MFCxx.DEF et MFCxxD.DEF). Uniquement ces ensemble sélectionné de points d’entrée (fonctions et données) sont exportés. Autres symboles, tels que les fonctions d’implémentation privée MFC ou les classes, ne sont pas exportées toutes les exportations sont effectuées par ordinal sans un nom de chaîne dans la table de noms résident ou non résident.

À l’aide de `class` **__declspec (dllexport)** peut être une alternative viable pour la création d’une DLL plus petits, mais dans le cas d’une DLL volumineuse comme MFC, la valeur par défaut exportation mécanisme a l’efficacité et la capacité de limites.

Cela signifie que toutes les nouveautés que nous pouvons package une grande quantité de fonctionnalités dans la version MFCxx.DLL est uniquement environ 800 Ko sans compromettre la quantité d’exécution ou la vitesse de chargement. MFCxx.DLL aurait été supérieure à 100K cette technique n’était pas utilisé. Cela rend également possible d’ajouter des points d’entrée supplémentaires à la fin de le. Fichier DEF pour permettre le contrôle de version simple sans compromettre l’efficacité de vitesse et la taille de l’exportation par ordinal. Révisions de version principale dans la bibliothèque de classes MFC modifie le nom de la bibliothèque. Autrement dit, MFC30. DLL est la DLL redistribuable contenant la version 3.0 de la bibliothèque de classes MFC. Une mise à niveau de cette DLL, par exemple, dans une hypothétique 3.1 de MFC, la DLL serait nommée MFC31. DLL à la place. Là encore, si vous modifiez le code source MFC pour produire une version personnalisée de la DLL de MFC, utilisez un autre nom (et préférence sans « MFC » dans le nom).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
