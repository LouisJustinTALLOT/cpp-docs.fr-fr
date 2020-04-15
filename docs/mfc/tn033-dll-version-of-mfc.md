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
ms.openlocfilehash: ad4cb883cfe7e397cf599d659afb02b23501dc5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370313"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033 : version DLL de MFC

Cette note décrit comment vous pouvez utiliser les bibliothèques de liens dynamiques MFCxx.DLL et MFCxxD.DLL (où x est le numéro de version MFC) ont partagé des bibliothèques de liens dynamiques avec les applications MFC et les DLL d’extension MFC. Pour plus d’informations sur les DLL MFC régulières, voir [Utiliser MFC dans le cadre d’un DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Cette note technique couvre trois aspects des LPL. Les deux derniers sont pour les utilisateurs les plus avancés:

- [Comment construire un MFC Extension DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Comment construire une application MFC qui utilise la version DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Comment les bibliothèques partagées de lien dynamique du MFC sont mises en œuvre](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Si vous êtes intéressé à construire un DLL à l’aide de MFC qui peut être utilisé avec des applications non-MFC (c’est ce qu’on appelle un DLL MFC régulier), consultez [la Note Technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Aperçu du support MFCxx.DLL : Terminologie et fichiers

**DLL MFC régulier**: Vous utilisez un DLL MFC régulier pour construire un DLL autonome à l’aide de certaines classes MFC. Les interfaces à travers la limite App/DLL sont des interfaces « C », et l’application client n’a pas besoin d’être une application MFC.

Il s’agit de la version de la prise en charge DLL pris en charge dans MFC 1.0. Il est décrit dans [la note technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) et l’échantillon MFC Advanced Concepts [DLLScreenCap](../overview/visual-cpp-samples.md).

> [!NOTE]
> À partir de la version 4.0 visualO, le terme **USRDLL** est obsolète et a été remplacé par un MFC DLL régulier qui relie statiquement à MFC. Vous pouvez également construire un DLL MFC régulier qui relie dynamiquement à MFC.

MFC 3.0 (et ci-dessus) prend en charge les LPL MFC réguliers avec toutes les nouvelles fonctionnalités, y compris les classes OLE et Database.

**AFXDLL**: C’est aussi ce qu’on appelle la version partagée des bibliothèques MFC. Il s’agit du nouveau support DLL ajouté dans MFC 2.0. La bibliothèque MFC elle-même se trouve dans un certain nombre de DLLs (décrit ci-dessous) et une application client ou DLL relie dynamiquement les DLL qu’elle nécessite. Les interfaces à travers la limite d’application/DLL sont des interfaces de classe CMD/MFC. L’application client doit être une application MFC. Cela prend en charge toutes les fonctionnalités MFC 3.0 (exception : UNICODE n’est pas pris en charge pour les classes de base de données).

> [!NOTE]
> À partir de la version 4.0 visualo, ce type de DLL est appelé « Extension DLL ».

Cette note utilisera MFCxx.DLL pour désigner l’ensemble MFC DLL, qui comprend :

- Debug: MFCxxD.DLL (combiné) et MFCSxxD.LIB (statique).

- Sortie: MFCxx.DLL (combiné) et MFCSxx.LIB (statique).

- Unicode Debug: MFCxxUD.DLL (combiné) et MFCSxxD.LIB (statique).

- Version Unicode: MFCxxU.DLL (combiné) et MFCSxxU.LIB (statique).

> [!NOTE]
> Le MFCSxx[U][D]. Les bibliothèques LIB sont utilisées en conjonction avec les DLLs partagés par le MFC. Ces bibliothèques contiennent du code qui doit être statiquement lié à l’application ou DLL.

Une application est reliée aux bibliothèques d’importation correspondantes :

- Debug: MFCxxD.LIB

- Sortie: MFCxx.LIB

- Débbug Unicode: MFCxxUD.LIB

- Communiqué Unicode: MFCxxU.LIB

Un " MFC Extension DLL " est un DLL construit sur MFCxx.DLL (et/ou les autres DLLs partagés par MFC). Ici, l’architecture des composants MFC entre en jeu. Si vous dérivez une classe utile d’une classe MFC, ou si vous construisez une autre boîte à outils MFC, vous pouvez la placer dans un DLL. Que DLL utilise MFCxx.DLL, tout comme l’application client ultime. Cela permet des classes de feuilles réutilisables, des classes de base réutilisables et des classes de vision/documents réutilisables.

## <a name="pros-and-cons"></a>Avantages et inconvénients

Pourquoi devriez-vous utiliser la version partagée de MFC

- L’utilisation de la bibliothèque partagée peut donner lieu à des applications plus petites (une application minimale qui utilise la majeure partie de la bibliothèque MFC est inférieure à 10K).

- La version partagée de MFC prend en charge les DLL d’extension MFC et les DLL MFC réguliers.

- La construction d’une application qui utilise les bibliothèques MFC partagées est plus rapide que la construction d’une application MFC statiquement liée parce qu’il n’est pas nécessaire de lier MFC lui-même. Cela est particulièrement vrai dans LES constructions **DEBUG** où le lien doit compacter les informations de débogé - en reliant avec un DLL qui contient déjà les informations de débogé, il ya moins d’informations de débbug à compacter dans votre application.

Pourquoi ne pas utiliser la version partagée de MFC :

- L’expédition d’une application qui utilise la bibliothèque partagée exige que vous expédiez la bibliothèque MFCxx.DLL (et d’autres) avec votre programme. MFCxx.DLL est librement redistributable comme de nombreux DLL, mais vous devez toujours installer le DLL dans votre programme SETUP. En outre, vous devez expédier le MSVCRTxx.DLL, qui contient la bibliothèque C-runtime qui est utilisé à la fois par votre programme et le MFC DLLs eux-mêmes.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Comment écrire un DLL D’extension MFC

Un DLL D’extension MFC est un DLL contenant des classes et des fonctions écrites pour embellir la fonctionnalité des classes MFC. Un DLL DLL D’extension MFC utilise les DLL MFC partagés de la même manière qu’une application l’utilise, avec quelques considérations supplémentaires :

- Le processus de construction est similaire à la construction d’une application qui utilise les bibliothèques MFC partagées avec quelques options supplémentaires de compilateur et de liaison.

- Un DLL D’extension MFC n’a pas de `CWinApp`classe dérivée.

- Un DLL D’extension MFC doit fournir un spécial `DllMain`. AppWizard fournit `DllMain` une fonction que vous pouvez modifier.

- Une DLL d’extension MFC fournira habituellement `CDynLinkLibrary` une routine d’initialisation pour `CRuntimeClass`créer un si l’extension MFC DLL souhaite exporter des es ou des ressources à l’application. Une catégorie `CDynLinkLibrary` dérivée de peut être utilisée si les données par application doivent être maintenues par l’extension MFC DLL.

Ces considérations sont décrites plus en détail ci-dessous. Vous devez également vous référer à l’échantillon MFC Advanced Concepts [DLLHUSK](../overview/visual-cpp-samples.md) car il illustre:

- Construire une application à l’aide des bibliothèques partagées. (DLLHUSK. EXE est une application MFC qui relie dynamiquement les bibliothèques MFC ainsi qu’à d’autres DLL.)

- Construction d’un DLL D’extension MFC. (Notez les drapeaux `_AFXEXT` spéciaux tels que ceux qui sont utilisés dans la construction d’une extension MFC DLL)

- Deux exemples de DLL DL DL DFC Extension. L’un montre la structure de base d’un MFC Extension DLL avec des exportations limitées (TESTDLL1) et l’autre montre l’exportation d’une interface de classe entière (TESTDLL2).

L’application client et toute extension MFC DL Doivent utiliser la même version de MFCxx.DLL. Vous devez suivre la convention de MFC DLL et fournir à la fois une version de débbug et de détail (/libération) de votre DLL d’extension MFC. Cela permet aux programmes clients de construire à la fois des versions de débbug et de détail de leurs applications et de les lier avec la version de débbug ou de détail appropriée de tous les DLL.

> [!NOTE]
> Étant donné que le nom de CMD mangling et les questions d’exportation, la liste d’exportation d’une extension MFC DLL peut être différente entre les versions de débogé et de détail des mêmes DLL et DLLs pour différentes plates-formes. Le commerce de détail MFCxx.DLL a environ 2000 points d’entrée exportés; le débbug MFCxxD.DLL a environ 3000 points d’entrée exportés.

### <a name="quick-note-on-memory-management"></a>Note rapide sur la gestion de la mémoire

La section intitulée « Memory Management », vers la fin de cette note technique, décrit la mise en œuvre de la MFCxx.DLL avec la version partagée de MFC. Les informations que vous devez savoir pour implémenter juste une extension MFC DLL est décrite ici.

MFCxx.DLL et tous les DLL d’extension MFC chargés dans l’espace d’adresse d’une application client utiliseront le même allouant de mémoire, le chargement des ressources et d’autres États « globaux » de MFC comme s’ils étaient dans la même application. Ceci est significatif parce que les bibliothèques DLL non-MFC et les DLLs MFC réguliers qui relient statiquement à MFC font exactement le contraire et ont chaque DLL allouant de son propre pool de mémoire.

Si une extension MFC DLL alloue la mémoire, alors cette mémoire peut se mêler librement à tout autre objet attribué à l’application. De plus, si une application qui utilise les bibliothèques MFC partagées s’écrase, la protection du système d’exploitation maintiendra l’intégrité de toute autre application MFC partageant le DLL.

De même, d’autres États « mondiaux » de MFC, comme le fichier exécutable actuel pour charger les ressources de, sont également partagés entre l’application client et tous les DLLs d’extension de MFC ainsi que MFCxx.DLL lui-même.

### <a name="building-an-mfc-extension-dll"></a>Construction d’une extension MFC DLL

Vous pouvez utiliser AppWizard pour créer un projet DLL d’extension MFC, et il générera automatiquement les paramètres appropriés de compilateur et de liaison. Il a également `DllMain` été générer une fonction que vous pouvez modifier.

Si vous convertissez un projet existant en une DLL d’extension MFC, commencez par les règles standard pour la construction d’une application en utilisant la version partagée de MFC, puis faites ce qui suit :

- Ajouter **/D_AFXEXT** aux drapeaux compilateur. Sur le dialogue Project Properties, sélectionnez le nœud C/CMD. Sélectionnez ensuite la catégorie Preprocessor. Ajoutez `_AFXEXT` au champ Define Macros, en séparant chacun des éléments avec des semi-colons.

- Retirez l’interrupteur **compilateur /Gy.** Sur le dialogue Project Properties, sélectionnez le nœud C/CMD. Sélectionnez ensuite la catégorie Génération de code. Assurez-vous que l’option « Activer le lien de niveau fonction » n’est pas activée. Cela facilitera l’exportation des classes parce que le lien ne supprimera pas les fonctions non réfrésuites. Si le projet original est utilisé pour construire un MFC DLL régulier relié statiquement à MFC, modifiez l’option de compilateur **/MT[d]** à **/MD[d]**.

- Construire une bibliothèque d’exportation avec l’option **/DLL** à LINK. Cela sera défini lorsque vous créerez une nouvelle cible, spécifiant Win32 Dynamic-Link Library comme type cible.

### <a name="changing-your-header-files"></a>Modification de vos fichiers d’en-tête

L’objectif d’une extension MFC DLL est généralement d’exporter certaines fonctionnalités communes à une ou plusieurs applications qui peuvent utiliser cette fonctionnalité. Cela se résume à l’exportation de classes et de fonctions globales qui sont disponibles pour vos applications client.

Pour ce faire, vous devez vous assurer que chacune des fonctions membres est marquée comme l’importation ou l’exportation, le cas échéant. Cela nécessite des `__declspec(dllexport)` déclarations spéciales: et `__declspec(dllimport)`. Lorsque vos classes sont utilisées par les applications client, vous voulez qu’elles soient déclarées comme `__declspec(dllimport)`. Lorsque l’extension MFC DLL lui-même est `__declspec(dllexport)`en cours de construction, ils doivent être déclarés comme . En outre, les fonctions doivent être effectivement exportées, de sorte que les programmes clients se lient à eux au moment de la charge.

Pour exporter toute votre `AFX_EXT_CLASS` classe, utilisez la définition de la classe. Cette macro est définie `__declspec(dllexport)` par `_AFXDLL` `_AFXEXT` le cadre comme `__declspec(dllimport)` quand `_AFXEXT` et est défini, mais défini comme quand n’est pas défini. `_AFXEXT`comme décrit ci-dessus, n’est défini que lors de la construction de votre extension MFC DLL. Par exemple :

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Ne pas exporter la classe entière

Parfois, vous pouvez exporter seulement les membres nécessaires de votre classe. Par exemple, si vous `CDialog`exportez une classe dérivée, vous n’aurez peut-être qu’à exporter le constructeur et l’appel. `DoModal` Vous pouvez exporter ces membres en utilisant le DLL . Fichier DEF, mais vous `AFX_EXT_CLASS` pouvez également utiliser de la même manière sur les membres individuels que vous devez exporter.

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

Lorsque vous faites cela, vous pouvez rencontrer un problème supplémentaire parce que vous n’exportez plus tous les membres de la classe. Le problème est dans la façon dont les macros MFC fonctionnent. Plusieurs des macros d’aide de MFC déclarent ou définissent réellement les membres de données. Par conséquent, ces membres de données devront également être exportés de votre DLL.

Par exemple, la macro DECLARE_DYNAMIC est définie comme suit lors de la construction d’une DLL d’extension MFC :

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

La ligne qui `AFX_DATA`commence " statique " déclare un objet statique à l’intérieur de votre classe. Pour exporter correctement cette classe et accéder aux informations en temps d’exécution d’un client . EXE, vous devez exporter cet objet statique. Parce que l’objet statique `AFX_DATA`est déclaré avec `AFX_DATA` le `__declspec(dllexport)` modificateur, vous n’avez qu’à définir pour être lors de la construction de votre DLL et le définir comme `__declspec(dllimport)` lors de la construction de votre client exécutable.

Comme nous `AFX_EXT_CLASS` l’avons vu plus haut, est déjà défini de cette façon. Vous avez juste besoin `AFX_DATA` de re-définir pour être le même que autour de `AFX_EXT_CLASS` votre définition de classe.

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

MFC utilise `AFX_DATA` toujours le symbole sur les éléments de données qu’il définit dans ses macros, de sorte que cette technique fonctionnera pour tous ces scénarios. Par exemple, il fonctionnera pour DECLARE_MESSAGE_MAP.

> [!NOTE]
> Si vous exportez toute la classe plutôt que des membres sélectionnés de la classe, les membres de données statiques sont automatiquement exportés.

Vous pouvez utiliser la même `CArchive` technique pour exporter automatiquement l’opérateur d’extraction pour les classes qui utilisent les DECLARE_SERIAL et IMPLEMENT_SERIAL macros. Exporter l’opérateur d’archives en entre crochetant les déclarations de classe (situé dans le . Fichier H) avec le code suivant :

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Limitations de _AFXEXT

Vous pouvez utiliser le symbole pré-processeur**AFXEXT** pour vos DLL d’extension MFC tant que vous n’avez pas plusieurs couches de DLL d’extension MFC. Si vous avez des DLL d’extension MFC qui appellent ou dérivent des classes dans votre propre DLL d’extension MFC, qui dérivent alors des classes MFC, vous devez utiliser votre propre symbole de préprocesseur pour éviter l’ambiguïté.

Le problème est que dans Win32, vous `__declspec(dllexport)` devez déclarer explicitement toutes les données `__declspec(dllimport)` comme si elles devaient être exportées à partir d’un DLL, et si elles doivent être importées d’un DLL. Lorsque vous `_AFXEXT`définissez, les en-têtes MFC s’assurent que cela `AFX_EXT_CLASS` est défini correctement.

Lorsque vous avez plusieurs couches, `AFX_EXT_CLASS` un symbole tel n’est pas suffisant, car une extension MFC DLL peut exporter de nouvelles classes ainsi que l’importation d’autres classes d’une autre extension MFC DLL. Afin de faire face à ce problème, utilisez un symbole préprocesseur spécial qui indique que vous construisez le DLL lui-même par rapport à l’utilisation de la DLL. Par exemple, imaginez deux DLL d’extension MFC, A.DLL, et B.DLL. Ils exportent chacun quelques classes en A.H et B.H, respectivement. B.DLL utilise les classes de A.DLL. Les fichiers d’en-tête ressemblerait à ceci:

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

Lorsque A.DLL est construit, il est construit avec **/DA_IMPL** et quand B.DLL est construit, il est construit avec **/DB_IMPL**. En utilisant des symboles distincts pour chaque DLL, CExampleB est exporté et CExampleA est importé lors de la construction B.DLL. CExampleA est exporté lors de la construction de L.A.DLL et importé lorsqu’il est utilisé par B.DLL (ou un autre client).

Ce type de superposition ne peut pas `AFX_EXT_CLASS` `_AFXEXT` être fait lors de l’utilisation des symboles intégrés et préprocesseurs. La technique décrite ci-dessus résout ce problème d’une manière semblable au mécanisme que MFC utilise lui-même lors de la construction de ses DLL d’extension OLE, Database et Network MFC.

### <a name="not-exporting-the-entire-class"></a>Ne pas exporter la classe entière

Encore une fois, vous devrez faire attention particulière lorsque vous n’exportez pas une classe entière. Vous devez vous assurer que les éléments de données nécessaires créés par les macros MFC sont exportés correctement. Cela peut être fait `AFX_DATA` en redéfinissant à la macro de votre classe spécifique. Cela devrait être fait chaque fois que vous n’exportez pas toute la classe.

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

Ce qui suit est le code exact que vous devez placer dans votre fichier source principale pour votre DLL d’extension MFC. Il devrait venir après la norme comprend. Notez que lorsque vous utilisez AppWizard pour créer des fichiers `DllMain` de démarrage pour une DLL d’extension MFC, il fournit un pour vous.

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

L’appel `AfxInitExtensionModule` pour capturer les modules`CRuntimeClass` runtime-classes (structures)`COleObjectFactory` ainsi que ses usines `CDynLinkLibrary` d’objets (objets) pour une utilisation plus tard lorsque l’objet est créé. L’appel (facultatif) pour permettre à `AfxTermExtensionModule` MFC de nettoyer le DLL d’extension MFC lorsque chaque processus se détache (ce `FreeLibrary` qui se produit lorsque le processus sort, ou lorsque le DLL est déchargé à la suite d’un appel) de la DLL d’extension MFC. Étant donné que la plupart des DLL d’extension MFC ne sont `AfxTermExtensionModule` pas chargées dynamiquement (généralement, elles sont liées par l’intermédiaire de leurs bibliothèques d’importation), l’appel à n’est généralement pas nécessaire.

Si votre application charge et libère dynamiquement les DLL `AfxTermExtensionModule` d’extension MFC, assurez-vous d’appeler comme indiqué ci-dessus. Assurez-vous également `AfxLoadLibrary` `AfxFreeLibrary` d’utiliser et (au `LoadLibrary` `FreeLibrary`lieu de fonctions Win32 et ) si votre application utilise plusieurs threads ou si elle charge dynamiquement une extension MFC DLL. L’utilisation `AfxLoadLibrary` et `AfxFreeLibrary` l’ouverture du code de démarrage et d’arrêt qui s’exécute lorsque l’extension MFC DLL est chargée et déchargée ne corrompt pas l’état mondial de MFC.

Le fichier d’en-tête AFXDLLX. H contient des définitions spéciales pour les structures utilisées dans `AFX_EXTENSION_MODULE` les `CDynLinkLibrary`DLL d’extension MFC, telles que la définition pour et .

*L’extension globaleDLL* doit être déclarée comme indiqué. Contrairement à la version 16 bits de MFC, vous pouvez allouer la mémoire et appeler les fonctions MFC `DllMain` pendant cette période, puisque le MFCxx.DLL est entièrement paraséminé au moment où vous êtes appelé.

### <a name="sharing-resources-and-classes"></a>Partage des ressources et des classes

Les DLL d’extension MFC simples n’ont besoin que d’exporter quelques fonctions à faible bande passante vers l’application client et rien de plus. DL plus d’interface utilisateur intensive peut vouloir exporter des ressources et des classes de C à l’application client.

Les ressources d’exportation se font par l’entremise d’une liste de ressources. Dans chaque application est une liste `CDynLinkLibrary` individuellement liée d’objets. Lorsque vous cherchez une ressource, la plupart des implémentations MFC`AfxGetResourceHandle`standard qui chargent les `CDynLinkLibrary` ressources examinent d’abord le module de ressources actuel ( ) et si elle n’est pas trouvée marchez la liste des objets qui tentent de charger la ressource demandée.

La création dynamique d’objets CMD donnés au nom de la classe C EST similaire. Le mécanisme de désétération des objets `CRuntimeClass` MFC doit faire enregistrer tous les objets afin qu’il puisse être reconstruit en créant dynamiquement l’objet Cmd du type requis en fonction de ce qui a été stocké plus tôt.

Si vous voulez que l’application client utilise les `DECLARE_SERIAL`classes de votre DLL d’extension MFC qui sont, alors vous devrez exporter vos classes pour être visible à l’application client. Cela se fait également `CDynLinkLibrary` en marchant sur la liste.

Dans le cas de l’échantillon MFC Advanced Concepts [DLLHUSK](../overview/visual-cpp-samples.md), la liste ressemble à:

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

Le MFCxx.DLL est généralement le dernier sur la liste des ressources et des classes. MFCxx.DLL inclut toutes les ressources MFC standard, y compris les chaînes rapides pour toutes les Œd de commande standard. Le placer à la queue de la liste permet aux DLL et à l’application client elle-même de ne pas avoir leur propre copie des ressources MFC standard, mais de s’appuyer plutôt sur les ressources partagées de la MFCxx.DLL.

La fusion des ressources et des noms de classe de tous les DLL dans l’espace de nom de l’application client a l’inconvénient que vous devez faire attention aux cartes d’ID ou aux noms que vous choisissez. Vous pouvez bien sûr désactiver cette fonctionnalité en n’exportant ni vos ressources ni un `CDynLinkLibrary` objet à l’application client. [L’échantillon DLLHUSK](../overview/visual-cpp-samples.md) gère l’espace de nom de ressource partagé en utilisant plusieurs fichiers d’en-tête. Voir [la note technique 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) pour plus de conseils sur l’utilisation de fichiers de ressources partagés.

### <a name="initializing-the-dll"></a>Initialiser le DLL

Comme mentionné ci-dessus, vous `CDynLinkLibrary` voudrez généralement créer un objet afin d’exporter vos ressources et vos classes vers l’application client. Vous devrez fournir un point d’entrée exporté pour initialiser le DLL. Minimalement, il s’agit d’une routine vide qui ne prend pas d’arguments et ne renvoie rien, mais il peut être tout ce que vous voulez.

Chaque application client qui veut utiliser votre DLL doit appeler cette routine d’initialisation, si vous utilisez cette approche. Vous pouvez également `CDynLinkLibrary` allouer `DllMain` cet `AfxInitExtensionModule`objet dans votre juste après l’appel .

La routine d’initialisation doit créer un `CDynLinkLibrary` objet dans le tas de l’application actuelle, câblé jusqu’à votre application MFC DLL informations. Cela peut être fait avec ce qui suit:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Le nom de routine, *InitXxxDLL* dans cet exemple, peut être tout ce que vous voulez. Il n’a pas besoin **d’être extern "C"**, mais ce faisant rend la liste d’exportation plus facile à maintenir.

> [!NOTE]
> Si vous utilisez votre DLL d’extension MFC à partir d’un DLL MFC régulier, vous devez exporter cette fonction d’initialisation. Cette fonction doit être appelée à partir de la DLL MFC régulière avant d’utiliser des classes ou des ressources DLL d’extension MFC.

### <a name="exporting-entries"></a>Entrées à l’exportation

La façon simple d’exporter `__declspec(dllimport)` vos `__declspec(dllexport)` classes est d’utiliser et sur chaque classe et fonction globale que vous souhaitez exporter. Cela le rend beaucoup plus facile, mais est moins efficace que de nommer chaque point d’entrée (décrit ci-dessous) puisque vous avez moins de contrôle sur les fonctions qui sont exportées et vous ne pouvez pas exporter les fonctions par ordinaire. TESTDLL1 et TESTDLL2 utilisent cette méthode pour exporter leurs entrées.

Une méthode plus efficace (et la méthode utilisée par MFCxx.DLL) est d’exporter chaque entrée à la main en nommant chaque entrée dans le . Fichier DEF. Étant donné que nous exportons des exportations sélectives de notre DLL (c’est-à-dire pas tout), nous devons décider quelles interfaces particulières nous souhaitons exporter. C’est difficile puisque vous devez spécifier les noms mutilés au lien sous la forme d’entrées dans le . Fichier DEF. N’exportez pas de classes de C à moins que vous n’ayez vraiment besoin d’avoir un lien symbolique pour cela.

Si vous avez essayé d’exporter des classes de C avec un . Fichier DEF avant, vous pouvez développer un outil pour générer cette liste automatiquement. Cela peut être fait à l’aide d’un processus de liaison en deux étapes. Liez votre DLL une fois sans exportations, et permettez au liaisonur de générer un . Fichier MAP. Lla. Fichier MAP peut être utilisé pour générer une liste de fonctions qui devraient être exportées, donc avec un certain réorganisation, il peut être utilisé pour générer vos entrées EXPORT pour votre . Fichier DEF. La liste d’exportation pour MFCxx.DLL et les DLL d’extension OLE et Database MFC, plusieurs milliers en nombre, a été générée avec un tel processus (bien qu’il ne soit pas complètement automatique et nécessite un certain réglage de la main de temps en temps).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs CDynLinkLibrary

Un DLL DLL d’extension MFC n’a pas d’objet `CWinApp`dérivé de ses propres; au lieu de `CWinApp`cela, il doit travailler avec l’objet dérivé de l’application client. Cela signifie que l’application client possède la pompe de message principal, la boucle de ralenti et ainsi de suite.

Si votre DLL DLL D’extension MFC doit conserver des `CDynLinkLibrary` données supplémentaires pour chaque application, vous pouvez tirer une nouvelle classe et la créer dans la routine InitXxDLL décrire ci-dessus. Lors de l’exécution, le DLL peut `CDynLinkLibrary` vérifier la liste des objets de l’application actuelle pour trouver celui de cette extension MFC particulière DLL.

### <a name="using-resources-in-your-dll-implementation"></a>Utilisation des ressources dans votre mise en œuvre DLL

Comme mentionné ci-dessus, la charge `CDynLinkLibrary` de ressources par défaut marchera la liste des objets à la recherche de la première EXE ou DLL qui a la ressource demandée. Toutes les API MFC ainsi que `AfxFindResourceHandle` tous les codes internes utilisent pour parcourir la liste des ressources pour trouver une ressource, peu importe où elle peut résider.

Si vous souhaitez charger uniquement les ressources à `AfxGetResourceHandle` partir `AfxSetResourceHandle` d’un endroit spécifique, utilisez les API et pour enregistrer l’ancienne poignée et définir la nouvelle poignée. Assurez-vous de restaurer l’ancienne poignée de ressources avant de revenir à l’application client. L’échantillon TESTDLL2 utilise cette approche pour charger explicitement un menu.

Marcher sur la liste a les inconvénients qu’il est légèrement plus lent et nécessite la gestion des gammes d’identification des ressources. Il a l’avantage qu’une application client qui relie à plusieurs DL DL d’extension MFC peut utiliser n’importe quelle ressource fournie par DLL sans avoir à spécifier la poignée d’instance DLL. `AfxFindResourceHandle`est une API utilisée pour la marche de la liste des ressources pour rechercher un match donné. Il prend le nom et le type d’une ressource et retourne la poignée de ressources où elle a été trouvée pour la première fois (ou NULL).

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Rédaction d’une application qui utilise la version DLL

### <a name="application-requirements"></a>Exigences en matière d’application

Une application qui utilise la version partagée de MFC doit suivre quelques règles simples :

- Il doit `CWinApp` avoir un objet et suivre les règles standard pour une pompe à messages.

- Il doit être compilé avec un ensemble de drapeaux compilateur requis (voir ci-dessous).

- Il doit établir des liens avec les bibliothèques d’importation MFCxx. En définissant les indicateurs de compilateur requis, les en-têtes MFC déterminent à l’heure du lien avec quelle bibliothèque l’application doit lier.

- Pour exécuter l’exécutable, MFCxx.DLL doit être sur le chemin ou dans le répertoire du système Windows.

### <a name="building-with-the-development-environment"></a>Construire avec l’environnement de développement

Si vous utilisez le fichier interne avec la plupart des défauts de paiement standard, vous pouvez facilement modifier le projet pour construire la version DLL.

L’étape suivante suppose que vous avez une application MFC fonctionnant correctement liée à NAFXCWD. LIB (pour débog) et NAFXCW. LIB (pour la vente au détail) et vous souhaitez le convertir pour utiliser la version partagée de la bibliothèque MFC. Vous exécutez l’environnement Visual CMD et avez un fichier de projet interne.

1. Sur le menu **des projets,** cliquez sur **Propriétés**. Dans la page **générale** sous **les défauts de projet**, définissez les classes de fondation Microsoft pour utiliser **MFC dans un DLL partagé** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Construire avec NMAKE

Si vous utilisez la fonction de remplissage externe du visual CMD, ou si vous utilisez directement NMAKE, vous devrez modifier votre makefile pour prendre en charge les options de compilateur et de liaison

Indicateurs de compilateur requis :

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

Les en-têtes MFC standard ont besoin de ce symbole pour être défini :

- **/MD** L’application doit utiliser la version DLL de la bibliothèque C run-time

Tous les autres drapeaux compilateur suivent les défauts de MFC (par exemple, _DEBUG pour le débogé).

Modifier la liste des bibliothèques. Changer NAFXCWD. LIB à MFCxxD.LIB et changer NAFXCW. LIB à MFCxx.LIB. Remplacer LIBC. LIB avec MSVCRT. Lib. Comme pour toute autre bibliothèque MFC, il est important que MFCxxD.LIB soit placé **devant** toutes les bibliothèques C-runtime.

**Ajouter/D_AFXDLL** à la fois à vos options de compilateur de ressources de détail et de débogé (celle qui compile réellement les ressources avec **/R**). Cela rend votre dernière exécutable plus petite en partageant les ressources qui sont présentes dans les DLL MFC.

Une reconstruction complète est nécessaire après que ces changements soient apportés.

### <a name="building-the-samples"></a>Génération des exemples

La plupart des programmes d’échantillons MFC peuvent être construits à partir de Visual CMD ou à partir d’un MAKEFILE compatible NMAKE partagé à partir de la ligne de commande.

Pour convertir l’un de ces échantillons à l’utilisation de MFCxx.DLL, vous pouvez charger le . Fichier MAK dans le Visual CMD et définissez les options du projet comme décrit ci-dessus. Si vous utilisez la version NMAKE, vous pouvez spécifier « AFXDLL-1 » sur la ligne de commande NMAKE et cela permettra de construire l’échantillon à l’aide des bibliothèques MFC partagées.

L’échantillon MFC Advanced Concepts [DLLHUSK](../overview/visual-cpp-samples.md) est construit avec la version DLL de MFC. Cet échantillon illustre non seulement comment construire une application liée à MFCxx.DLL, mais il illustre également d’autres caractéristiques de l’option d’emballage MFC DLL telles que les DLL DL DFC d’extension de MFC décrites plus tard dans cette note technique.

### <a name="packaging-notes"></a>Notes d’emballage

La version de détail des DLL (MFCxx[U]. DLL) sont librement redistributables. La version déboptée des DLL ne sont pas librement redistributables et ne doivent être utilisées que lors du développement de votre application.

Les DLL de déboguer sont fournis avec des informations de débogage. En utilisant le débbugger Visual CMD, vous pouvez retracer l’exécution de votre application ainsi que la DLL. The Release DLLs (MFCxx[U]. DLL) ne contiennent pas d’informations de débogage.

Si vous personnalisez ou reconstruisez les LPL, alors vous devriez les appeler autre chose que "MFCxx" Le fichier MFC SRC MFCDLL. MAK décrit les options de construction et contient la logique pour renommer le DLL. Le changement de nom des fichiers est nécessaire, car ces DLL sont potentiellement partagés par de nombreuses applications MFC. Le fait que votre version personnalisée des LPL MFC remplace ceux installés sur le système peut casser une autre application MFC à l’aide des DLL MFC partagées.

La reconstruction des LPL MFC n’est pas recommandée.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Comment le MFCxx.DLL est implémenté

La section suivante décrit comment le MFC DLL (MFCxx.DLL et MFCxxD.DLL) est mis en œuvre. Comprendre les détails ici ne sont pas non plus importants si tout ce que vous voulez faire est d’utiliser le MFC DLL avec votre application. Les détails ici ne sont pas essentiels pour comprendre comment écrire une extension MFC DLL, mais la compréhension de cette implémentation peut vous aider à écrire votre propre DLL.

### <a name="implementation-overview"></a>Aperçu de la mise en œuvre

Le MFC DLL est vraiment un cas spécial d’un DLL DLL D’extension MFC comme décrit ci-dessus. Il a un très grand nombre d’exportations pour un grand nombre de classes. Il ya quelques choses supplémentaires que nous faisons dans le MFC DLL qui le rendent encore plus spécial qu’une extension régulière MFC DLL.

### <a name="win32-does-most-of-the-work"></a>Win32 Fait la plupart du travail

La version 16 bits de MFC avait besoin d’un certain nombre de techniques spéciales, y compris les données par application sur le segment de la pile, des segments spéciaux créés par un code d’assemblage 80x86, des contextes d’exception par processus et d’autres techniques. Win32 prend directement en charge les données par processus dans un DLL, ce que vous voulez la plupart du temps. Pour la plupart MFCxx.DLL est juste NAFXCW. LIB emballé dans un DLL. Si vous regardez le code source MFC, vous trouverez très peu #ifdef _AFXDLL, car il ya très peu de cas spéciaux qui doivent être faites. Les cas spéciaux qui sont là sont spécifiquement pour traiter avec Win32 sur Windows 3.1 (autrement connu sous le nom Win32s). Win32s ne prend pas en charge directement les données DLL par processus, de sorte que le MFC DLL doit utiliser les API Win32 de stockage par fil local (TLS) pour obtenir le traitement des données locales.

### <a name="impact-on-library-sources-additional-files"></a>Impact sur les sources de bibliothèque, fichiers additionnels

L’impact de la version **_AFXDLL** sur les sources et en-têtes normaux de la bibliothèque de classe MFC est relativement mineur. Il existe un fichier version spéciale (AFXV_DLL. H) ainsi qu’un fichier d’en-tête supplémentaire (AFXDLL_. H) inclus par le principal AFXWIN. H en-tête. Le AFXDLL_. H en-tête comprend la `CDynLinkLibrary` classe `_AFXDLL` et d’autres détails de mise en œuvre des deux applications et MFC Extension DLLs. L’AFXDLLX. H en-tête est prévu pour la construction MFC Extension DLLs (voir ci-dessus pour plus de détails).

Les sources régulières à la bibliothèque MFC de MFC `_AFXDLL` SRC ont un code conditionnel supplémentaire en vertu de la #ifdef. Un fichier source supplémentaire (DLLINIT. CPP) contient le code d’initialisation DLL supplémentaire et d’autres colles pour la version partagée de MFC.

Afin de construire la version partagée de MFC, des fichiers supplémentaires sont fournis. (Voir ci-dessous pour plus de détails sur la façon de construire le DLL.)

- Deux. Les fichiers DEF sont utilisés pour l’exportation des points d’entrée MFC DLL pour les versions de débbug (MFCxxD.DEF) et de version (MFCxx.DEF) de la DLL.

- Un. Fichier RC (MFCDLL. RC) contient toutes les ressources MFC standard et une ressource VERSIONINFO pour le DLL.

- Un. Fichier CLW (MFCDLL. CLW) est fourni pour permettre la navigation des classes MFC en utilisant ClassWizard. Remarque : cette fonctionnalité n’est pas particulière à la version DLL de MFC.

### <a name="memory-management"></a>Gestion de la mémoire

Une application utilisant MFCxx.DLL utilise un alloueur de mémoire commun fourni par MSVCRTxx.DLL, le DLL C-runtime partagé. L’application, toutes les DLL d’extension MFC, ainsi que les DLLs MFC eux-mêmes utilisent cet alloueur de mémoire partagée. En utilisant un DLL partagé pour l’allocation de mémoire, les DLL MFC peuvent allouer la mémoire qui est plus tard libérée par l’application ou vice versa. Étant donné que l’application et le DLL doivent utiliser le même alloueur, vous ne devez pas remplacer l’opérateur mondial **Cmd nouveau** ou **l’opérateur supprimer**. Les mêmes règles s’appliquent au reste des routines d’allocation de mémoire de durée de C (comme **malloc**, **réaffectation**, **gratuit,** et d’autres).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Ordinals et classe __declspec (dllexport) et DLL nommant

Nous n’utilisons `class` pas la fonctionnalité **__declspec (dllexport)** du compilateur C. Au lieu de cela, une liste des exportations est incluse avec les sources de bibliothèque de classe (MFCxx.DEF et MFCxxD.DEF). Seuls ces ensembles de points d’entrée sélectionnés (fonctions et données) sont exportés. Autres symboles, tels que les fonctions ou les classes privées de mise en œuvre de MFC, ne sont pas exportés Toutes les exportations sont effectuées par ordinaire sans nom de chaîne dans la table de nom résidente ou non-résidente.

L’utilisation `class` **de __declspec (dllexport)** peut être une alternative viable pour la construction de LPL plus petits, mais dans le cas d’un grand DLL comme MFC, le mécanisme d’exportation par défaut a des limites d’efficacité et de capacité.

Ce que tout cela signifie, c’est que nous pouvons emballer une grande quantité de fonctionnalités dans la version MFCxx.DLL qui est seulement autour de 800 KB sans compromettre beaucoup d’exécution ou de vitesse de chargement. MFCxx.DLL aurait été 100K plus grand si cette technique n’avait pas été utilisée. Cela permet également d’ajouter des points d’entrée supplémentaires à la fin de la . Fichier DEF pour permettre la version simple sans compromettre la vitesse et l’efficacité de taille de l’exportation par ordinaire. Les révisions de versions majeures dans la bibliothèque de classe MFC changeront le nom de la bibliothèque. C’est-à-dire, MFC30. DLL est le DLL redistributable contenant la version 3.0 de la bibliothèque de classe MFC. Une mise à niveau de ce DLL, par exemple, dans un hypothétique MFC 3.1, le DLL serait nommé MFC31. DLL à la place. Encore une fois, si vous modifiez le code source MFC pour produire une version personnalisée de la DLL MFC, utilisez un nom différent (et de préférence un nom sans "MFC" dans le nom).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
