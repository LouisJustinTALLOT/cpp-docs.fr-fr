---
title: 'TN033 : Version DLL de MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dll
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a247ffc36b3e0eb3e52c6f04949c693597d73064
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385240"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033 : version DLL de MFC
Cette note décrit comment vous pouvez utiliser le partagées MFCxx.DLL et MFCxxD.DLL (où x est le numéro de version MFC) des bibliothèques de liens dynamiques avec les applications MFC et les DLL d’extension MFC. Pour plus d’informations sur les DLL régulières MFC, consultez [à l’aide de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
 Cette note technique couvre trois aspects de la DLL. Les deux derniers sont pour les utilisateurs expérimentés :  
  
- [Comment vous générez une DLL d’Extension MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)  
  
- [Comment vous générez une application MFC qui utilise la version DLL de MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)  
  
- [Comment MFC partagée des bibliothèques de liens dynamiques sont implémentées.](#_mfcnotes_how_the_mfc30.dll_is_implemented)  
  
 Si vous êtes intéressé de la génération d’une DLL à l’aide de MFC, qui peut être utilisé avec les applications non-MFC (cela s’appelle une DLL MFC normale), reportez-vous à [Note technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Vue d’ensemble de la prise en charge MFCxx.DLL : la terminologie et les fichiers  
 **DLL MFC normale**: une DLL MFC standard vous permet de créer une DLL autonome à l’aide de certaines des classes MFC. Interfaces au-delà des limites d’application/DLL sont des interfaces de « C », et l’application cliente n’a pas à être une application MFC.  
  
 Il s’agit de la version de prise en charge des DLL pris en charge dans MFC 1.0. Il est décrit dans [Note technique 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) et l’exemple MFC Advanced Concepts [DLLScreenCap](../visual-cpp-samples.md).  
  
> [!NOTE]
>  À compter de Visual C++ version 4.0, le terme **USRDLL** est obsolète et a été remplacé par une DLL régulière MFC qui lie statiquement à MFC. Vous pouvez également générer une DLL MFC qui lie dynamiquement à MFC standard.  
  
 MFC 3.0 (et versions ultérieures) prend en charge les DLL régulières MFC avec de nouvelles fonctionnalités, notamment les classes OLE et de la base de données.  
  
 **AFXDLL**: il est également appelé à la version partagée des bibliothèques MFC. Il s’agit de la nouvelle DLL prend désormais en charge dans MFC 2.0. La bibliothèque MFC elle-même est le nombre de DLL (décrites ci-dessous) et une application cliente ou une DLL liée de manière dynamique les DLL dont il a besoin. Interfaces au-delà des limites d’application/DLL sont C + c++ / interfaces de classe MFC. L’application cliente doit être une application MFC. Il prend en charge toutes les fonctionnalités de MFC 3.0 (exception : UNICODE n’est pas prise en charge pour les classes de base de données).  
  
> [!NOTE]
>  À compter de Visual C++ version 4.0, ce type de DLL est appelée pour une « DLL d’Extension. »  
  
 Cette note utilisera MFCxx.DLL pour faire référence à l’ensemble du jeu de DLL MFC, qui inclut :  
  
-   Debug : MFCxxD.DLL (combinés) et MFCSxxD.LIB (statique).  
  
-   Version : MFCxx.DLL (combinés) et MFCSxx.LIB (statique).  
  
-   Unicode Debug : MFCxxUD.DLL (combinés) et MFCSxxD.LIB (statique).  
  
-   Version d’Unicode : MFCxxU.DLL (combinés) et MFCSxxU.LIB (statique).  
  
> [!NOTE]
>  Le MFCSxx [U] [D]. Lib sont utilisées en conjonction avec la bibliothèque MFC des DLL partagées. Ces bibliothèques contiennent le code qui doit être lié statiquement à l’application ou la DLL.  
  
 Une application des liens vers les bibliothèques d’importation correspondante :  
  
-   Déboguer : MFCxxD.LIB  
  
-   Mise en production : MFCxx.LIB  
  
-   Debug Unicode : MFCxxUD.LIB  
  
-   Version d’Unicode : MFCxxU.LIB  
  
 Une « DLL d’Extension MFC » est une DLL basée sur les objets MFCxx.DLL (et/ou l’autres MFC des DLL partagées). Ici l’architecture des composants MFC intervient. Si vous dérivez une classe d’utile à partir d’une classe MFC, ou générez un autre type MFC toolkit, vous pouvez le placer dans une DLL. Que les DLL utilise MFCxx.DLL, comme l’application cliente ultimate. Ainsi, les classes de feuille réutilisables, les classes de base réutilisables et classes de document/vue réutilisables.  
  
## <a name="pros-and-cons"></a>Avantages et inconvénients  
 Pourquoi devez-vous utiliser la version partagée de MFC  
  
-   À l’aide de la bibliothèque partagée, vous risquez de petites applications (une application minimale qui utilise la plupart de la bibliothèque MFC est inférieure à 10 Ko).  
  
-   La version partagée de MFC prend en charge les DLL d’Extension MFC et les DLL régulières MFC.  
  
-   Création d’une application qui utilise les bibliothèques MFC partagées est plus rapide que la création d’une application MFC liée statiquement, car il n’est pas nécessaire de lier l’application MFC elle-même. Cela est particulièrement vrai dans **déboguer** builds où l’éditeur de liens doit compacter les informations de débogage, en liaison avec une DLL qui contient déjà les informations de débogage, il est moins les informations de débogage à compacter dans votre application.  
  
 Pourquoi devez vous pas pas utiliser la version partagée de MFC :  
  
-   Copie d’une application qui utilise la bibliothèque partagée nécessite que vous expédiez le MFCxx.DLL (et autres) bibliothèque avec votre programme. MFCxx.DLL est librement redistribuable comme nombre de DLL, mais vous devez toujours installer la DLL dans votre programme d’installation. En outre, vous devez expédier le MSVCRTxx.DLL, qui contient la bibliothèque runtime C qui est utilisée à la fois par votre programme et les DLL MFC elles-mêmes.  
  
##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Comment écrire une DLL d’Extension MFC  
 Une DLL d’Extension MFC est une DLL qui contient les classes et fonctions écrites pour améliorer les fonctionnalités des classes MFC. Une DLL d’Extension MFC utilise la DLL MFC partagée de la même façon qu’une application utilise, avec quelques considérations supplémentaires :  
  
-   Le processus de génération est similaire à la création d’une application qui utilise les bibliothèques MFC partagées avec quelques autres options du compilateur et l’éditeur de liens.  
  
-   Une DLL d’Extension MFC n’a pas un `CWinApp`-classe dérivée.  
  
-   Une DLL d’Extension MFC doit fournir un spécial `DllMain`. AppWizard fournit un `DllMain` fonction que vous pouvez modifier.  
  
-   Une DLL d’Extension MFC fournit généralement une routine d’initialisation pour créer un **CDynLinkLibrary** si l’extension MFC DLL souhaite exporter `CRuntimeClass`es ou ressources à l’application. Une classe dérivée de **CDynLinkLibrary** peut être utilisée si les données d’application doivent être gérées par la DLL d’extension MFC.  
  
 Ces considérations sont décrits plus en détail ci-dessous. Vous devez également vous reporter à l’exemple MFC Advanced Concepts [DLLHUSK](../visual-cpp-samples.md) , car il illustre :  
  
-   Création d’une application en utilisant les bibliothèques partagées. (DLLHUSK. EXE est une application MFC liée de manière dynamique aux bibliothèques MFC, ainsi que les autres DLL).  
  
-   Génération d’une DLL d’Extension MFC. (Notez les indicateurs spéciaux tels que `_AFXEXT` qui sont utilisés dans la création d’une DLL d’extension MFC)  
  
-   Deux exemples de DLL d’Extension MFC. Un élément indique la structure de base d’une DLL d’Extension MFC avec des exportations limitées (TESTDLL1) et l’autre montre exportation d’une interface de classe entière (TESTDLL2).  
  
 L’application cliente et toutes les DLL d’extension MFC doivent utiliser la même version de MFCxx.DLL. Vous devez suivre la convention de DLL MFC et fournir à la fois un type de débogage et de vente au détail (/ release) version de la DLL d’extension MFC. Cela permet aux programmes de client pour générer les versions debug et vente au détail de leurs applications et de les lier avec le débogage ou la version commerciale de toutes les DLL.  
  
> [!NOTE]
>  Étant donné que C++ nom altération et exporter des problèmes, la liste d’exportation à partir d’une DLL d’extension MFC peut être différente entre les versions debug et la vente au détail de la même DLL et les DLL pour les différentes plateformes. La vente au détail MFCxx.DLL a environ 2000 exporté des points d’entrée ; le débogage MFCxxD.DLL a environ 3000 points d’entrée exportés.  
  
### <a name="quick-note-on-memory-management"></a>Note rapide sur la gestion de la mémoire  
 La section intitulée « Gestion de mémoire » à la fin de cette note technique, décrit l’implémentation de MFCxx.DLL avec la version partagée de MFC. Les informations que vous devez connaître pour implémenter simplement une extension MFC que DLL est décrit ici.  
  
 MFCxx.DLL et toutes les DLL d’extension MFC chargés dans l’espace d’adressage d’une application cliente utiliseront l’allocateur de mémoire de même, le chargement des ressources et autres États « globaux » MFC comme s’ils étaient dans la même application. Ceci est important car les bibliothèques de DLL non - MFC et les DLL MFC standard qui lient statiquement à MFC faisons exactement le contraire et que chaque DLL affecte en dehors de son propre pool de mémoire.  
  
 Si une DLL d’extension MFC alloue de la mémoire, cette mémoire peut alors être librement mélangée avec tout autre objet alloué par l’application. En outre, si une application qui utilise les bibliothèques MFC partagées tombe en panne, la protection du système d’exploitation conserve l’intégrité de toute autre application MFC partageant la DLL.  
  
 De même les autres États « globaux » MFC, tels que le fichier exécutable en cours pour charger les ressources à partir, sont également partagés entre l’application cliente et toutes les DLL d’extension MFC ainsi MFCxx.DLL lui-même.  
  
### <a name="building-an-mfc-extension-dll"></a>Création d’une DLL d’extension MFC  
 Vous pouvez utiliser AppWizard pour créer un projet DLL d’extension MFC, et il génère automatiquement les paramètres de l’éditeur de liens et le compilateur approprié. Il a été également générer un `DllMain` fonction que vous pouvez modifier.  
  
 Si vous convertissez un projet existant à une DLL d’extension MFC, commencer par les règles standard pour la création d’une application à l’aide de la version partagée de MFC, puis procédez comme suit :  
  
-   Ajouter **/D_AFXEXT** pour les indicateurs de compilateur. Dans la boîte de dialogue Propriétés du projet, sélectionnez le nœud C/C++. Puis sélectionnez la catégorie de préprocesseur. Ajouter `_AFXEXT` au champ, définir des Macros séparant chacun des éléments par des points-virgules.  
  
-   Supprimer le **/Gy** commutateur du compilateur. Dans la boîte de dialogue Propriétés du projet, sélectionnez le nœud C/C++. Puis sélectionnez la catégorie de la génération de Code. Assurez-vous que l’option « Activer la liaison au niveau des fonctions » n’est pas activée. Cela rend plus facile exporter des classes, car l’éditeur de liens ne supprime pas les fonctions non référencées. Si le projet d’origine est utilisé pour créer une expression régulière DLL MFC lié statiquement à MFC, modifier le **/MT [d]** l’option du compilateur **/MD [d]**.  
  
-   Générer une bibliothèque d’exportation avec les **/DLL** option au lien. Cette description est définie lorsque vous créez une nouvelle cible, la spécification de bibliothèque de liens dynamiques Win32 comme type cible.  
  
### <a name="changing-your-header-files"></a>La modification de vos fichiers d’en-tête  
 L’objectif d’une DLL d’extension MFC consiste généralement à exporter des fonctionnalités communes pour une ou plusieurs applications qui peuvent utiliser cette fonctionnalité. Cela revient à l’exportation des classes et des fonctions globales qui sont disponibles pour vos applications clientes.  
  
 Pour ce faire, vous devez vous assurer que chacun des fonctions membres comme étant importer ou exporter selon le cas. Cela nécessite de déclarations spéciale : **__declspec (dllexport)** et **__declspec (dllimport)**. Lorsque vos classes sont utilisées par les applications clientes, vous souhaitez qu’ils être déclaré en tant que **__declspec (dllimport)**. Lorsque la DLL d’extension MFC est en cours de génération, ils doivent être déclarés comme **__declspec (dllexport)**. En outre, les fonctions doivent être réellement exportées, afin que les programmes clients procéder à une liaison au moment du chargement.  
  
 Pour exporter votre classe entière, utilisez **AFX_EXT_CLASS** dans la définition de classe. Cette macro est définie par l’infrastructure en tant que **__declspec (dllexport)** lorsque **_AFXDLL** et `_AFXEXT` est défini, mais définis comme **__declspec (dllimport)** lorsque `_AFXEXT` n’est pas défini. `_AFXEXT` comme décrit ci-dessus, est définie uniquement lors de la génération de la DLL d’extension MFC. Par exemple :  
  
```  
class AFX_EXT_CLASS CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
### <a name="not-exporting-the-entire-class"></a>Exportez ne pas la classe entière  
 Vous pouvez être amené à exporter uniquement les membres nécessaires individuels de votre classe. Par exemple, si vous exportez un `CDialog`-classe dérivée, vous devrez peut-être uniquement exporter le constructeur et le `DoModal` appeler. Vous pouvez exporter ces membres à l’aide de la DLL. Fichier DEF, mais vous pouvez également utiliser **AFX_EXT_CLASS** de la même façon sur les membres individuels, vous devez exporter.  
  
 Par exemple :  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
    AFX_EXT_CLASS CExampleDialog();
AFX_EXT_CLASS int DoModal();
*// rest of class definition  
 .  
 .  
 .  
};  
```  
  
 Lorsque vous effectuez cette opération, vous risquez de rencontrer un autre problème, car vous n’exportez plus tous les membres de la classe. Le problème réside dans le fonctionnement des macros MFC. Plusieurs macros d’assistance MFC réellement déclarent ou définissent des membres de données. Par conséquent, ces membres de données devez également être exportées à partir de votre DLL.  
  
 Par exemple, le `DECLARE_DYNAMIC` macro est défini comme suit lors de la création d’une DLL d’extension MFC :  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
    static CRuntimeClass* PASCAL _GetBaseClass();

\  
    public: \  
    static AFX_DATA CRuntimeClass class##class_name; \  
    virtual CRuntimeClass* GetRuntimeClass() const;

\  
```  
  
 La ligne qui commence par « statique `AFX_DATA`» déclare un objet statique à l’intérieur de votre classe. Pour exporter cette classe correctement et accéder aux informations d’exécution à partir d’un client. EXE, vous devez exporter cet objet statique. Car l’objet statique est déclaré avec le modificateur `AFX_DATA`, vous ne devez définir `AFX_DATA` être **__declspec (dllexport)** lors de la création de la DLL et définir en tant que **__declspec (dllimport)** lors de la génération de l’exécutable client.  
  
 Comme expliqué ci-dessus, **AFX_EXT_CLASS** est déjà définie de cette façon. Il vous suffit de redéfinir `AFX_DATA` pour être le même que **AFX_EXT_CLASS** autour de votre définition de classe.  
  
 Par exemple :  
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
class CExampleView : public CView  
{  
    DECLARE_DYNAMIC() *// ... class definition ...  
};  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 MFC utilise toujours le `AFX_DATA` symbole sur les éléments de données qu’elles définissent dans leurs macros, pour cette technique fonctionne pour tous ces scénarios. Par exemple, elle fonctionnera pour `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Si vous exportez la classe entière plutôt que les membres sélectionnés de la classe, les données membres statiques sont exportés automatiquement.  
  
 Vous pouvez utiliser la même technique pour exporter automatiquement la `CArchive` opérateur d’extraction pour les classes qui utilisent la `DECLARE_SERIAL` et `IMPLEMENT_SERIAL` macros. Exporter l’opérateur de l’archive en associant les déclarations de classe (situé dans le. Fichier de H) avec le code suivant :  
  
```  
#undef AFX_API  
#define AFX_API AFX_EXT_CLASS  
 
<your class declarations here>  
 
#undef AFX_API  
#define AFX_API  
```  
  
### <a name="limitations-of-afxext"></a>Limitations de _AFXEXT  
 Vous pouvez utiliser la _**AFXEXT** symbole de préprocesseur pour votre tant que vous n’avez pas plusieurs couches de DLL d’extension MFC des DLL d’extension MFC. Si vous avez qui appellent ou dérivent des classes dans votre propre MFC DLL d’extension, lesquelles dérivent ensuite les classes MFC, les DLL d’extension MFC, vous devez utiliser votre propre symbole de préprocesseur pour éviter toute ambiguïté.  
  
 Le problème est que dans Win32, vous devez déclarer explicitement toutes les données en tant que **__declspec (dllexport)** s’il doit être exporté à partir d’une DLL, et **__declspec (dllimport)** s’il doit être importé à partir d’une DLL. Lorsque vous définissez `_AFXEXT`, les en-têtes MFC vous assurer que **AFX_EXT_CLASS** est correctement défini.  
  
 Lorsque vous avez plusieurs couches, un symbole comme **AFX_EXT_CLASS** n’est pas suffisant, dans la mesure où une DLL d’extension MFC peut exporter de nouvelles classes, ainsi que l’importation d’autres classes à partir d’une autre DLL d’extension MFC. Pour résoudre ce problème, utilisez un symbole de préprocesseur spécial qui indique que vous générez la DLL mais plutôt à l’aide de la DLL. Par exemple, imaginez deux DLL d’extension MFC,.dll et B.DLL. Elles exportent certaines classes dans A.H et B.H, respectivement. B.DLL utilise les classes de.dll. Les fichiers d’en-tête ressemblerait à ceci :  
  
```  
/* A.H */  
#ifdef A_IMPL  
 #define CLASS_DECL_A   __declspec(dllexport)  
#else  
 #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
 
/* B.H */  
#ifdef B_IMPL  
 #define CLASS_DECL_B   __declspec(dllexport)  
#else  
 #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition .. };  
```  
  
 Lorsque.dll est généré, il est généré avec **/D A_IMPL** et lorsque B.DLL est générée, elle est générée avec **/D B_IMPL**. En utilisant des symboles séparés pour chaque DLL, CExampleB est exporté et CExampleA est importé lors de la génération de B.DLL. CExampleA est exporté lors de la génération.dll et importé lorsqu’il est utilisé par B.DLL (ou un autre client).  
  
 Ce type de superposition ne peut pas être effectué lors de l’utilisation de la fonction intégrée **AFX_EXT_CLASS** et `_AFXEXT` symboles de préprocesseur. La technique décrite ci-dessus résout ce problème de manière pas contrairement au que mécanisme d’application MFC elle-même utilise lors de la génération de la DLL d’extension réseau MFC OLE et de base de données.  
  
### <a name="not-exporting-the-entire-class"></a>Exportez ne pas la classe entière  
 Là encore, vous devez prendre un soin particulier lorsque vous n’exportez pas une classe entière. Vous devez vous assurer que les éléments de données nécessaires créés par les macros MFC sont exportés correctement. Cela est possible en définissant nouveau **AFX_DATA** à la macro de votre classe spécifique. Cela doit être effectuée à tout moment, que vous n’exportez pas la classe entière.  
  
 Par exemple :  
  
```  
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
*//class definition   
 .  
 .  
 .  
};  
 
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### <a name="dllmain"></a>DllMain  
 Voici le code exact que vous placez dans votre fichier source principal pour la DLL d’extension MFC. Il doit être une fois que la norme inclut. Notez que lorsque vous utilisez AppWizard pour créer des fichiers de démarrage pour une DLL d’extension MFC, il fournit un `DllMain` pour vous.  
  
```  
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
  
 L’appel à `AfxInitExtensionModule` capture les classes d’exécution modules (`CRuntimeClass` structures), ainsi que ses fabriques d’objets (`COleObjectFactory` objets) à utiliser ultérieurement, lorsque le **CDynLinkLibrary** objet est créé. L’appel (facultatif) `AfxTermExtensionModule` permet de MFC nettoyer la DLL d’extension MFC lorsque chaque processus détache (ce qui se produit quand le processus se termine, ou lorsque la DLL est déchargée à la suite d’un **FreeLibrary** appeler) à partir de la DLL d’extension MFC . Depuis la plupart des DLL ne sont pas chargées dynamiquement d’extension MFC (en règle générale, ils sont liés via leurs bibliothèques d’importation), l’appel à `AfxTermExtensionModule` est généralement pas nécessaire.  
  
 Si votre application est chargée et libère dynamiquement la DLL d’extension MFC, veillez à appeler `AfxTermExtensionModule` comme indiqué ci-dessus. Veillez également à utiliser `AfxLoadLibrary` et `AfxFreeLibrary` (au lieu des fonctions Win32 **LoadLibrary** et **FreeLibrary**) si votre application utilise plusieurs threads ou s’il charge dynamiquement une MFC DLL d’extension. À l’aide de `AfxLoadLibrary` et `AfxFreeLibrary` permet de s’assurer que le code de démarrage et d’arrêt qui s’exécute lorsque la DLL d’extension MFC est chargé et déchargé n’altère pas l’état global des MFC.  
  
 Le fichier d’en-tête AFXDLLX. H contient des définitions spéciales pour les structures utilisées dans les DLL d’extension MFC, telles que la définition de `AFX_EXTENSION_MODULE` et **CDynLinkLibrary**.  
  
 Global *extensionDLL* doit être déclarée comme indiqué. Contrairement à la version 16 bits de MFC, vous pouvez allouer de la mémoire et appeler des fonctions MFC pendant ce temps, étant donné que la MFCxx.DLL est entièrement initialisé par le temps votre `DllMain` est appelée.  
  
### <a name="sharing-resources-and-classes"></a>Partage des ressources et des Classes  
 DLL d’extension MFC simples doivent uniquement exporter les quelques fonctions de faible bande passante à l’application cliente et rien de plus. DLL de beaucoup plus d’interface utilisateur souhaiterez peut-être exporter des ressources et des classes C++ à l’application cliente.  
  
 Exportation de ressources s’effectue via une liste de ressources. Dans chaque application est une seule liste liée de **CDynLinkLibrary** objets. Lors de la recherche d’une ressource, la plupart des implémentations MFC standard qui chargent des ressources examinent d’abord en le module de ressources en cours (`AfxGetResourceHandle`) et s’il en n'existe pas de parcours de la liste des **CDynLinkLibrary** objets tente de charger le ressource demandée.  
  
 La création dynamique d’objets C++ étant donné un nom de classe C++ est similaire. Le mécanisme de la désérialisation d’objets MFC doit avoir tous les `CRuntimeClass` objets enregistrés afin qu’il puisse reconstruire en créant dynamiquement des objets C++ du type requis en fonction de ce qui a été stocké précédemment.  
  
 Si vous souhaitez que l’application cliente pour utiliser les classes dans votre DLL d’extension MFC qui sont `DECLARE_SERIAL`, vous devrez exporter vos classes pour être visible à l’application cliente. Cela est également assurée en parcourant le **CDynLinkLibrary** liste.  
  
 Dans le cas de l’exemple MFC Advanced Concepts [DLLHUSK](../visual-cpp-samples.md), la liste ressemble à ceci :  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
 |      |  
    TESTDLL2.DLL TESTDLL2.DLL  
 |      |  
    TESTDLL1.DLL TESTDLL1.DLL  
 |      |  
 |      |  
    MFC90D.DLL MFC90.DLL  
```  
  
 MFCxx.DLL occupe généralement la dernière sur la ressource et la liste de classes. MFCxx.DLL inclut toutes les ressources MFC standards, y compris les chaînes d’invite pour tous les ID de commande standard. Permet de placer à la fin de la liste de DLL et l’application du client de ne pas avoir un leur propre copie des ressources MFC standards, mais au s’appuient sur les ressources partagées dans la MFCxx.DLL à la place.  
  
 Fusionner les ressources et les noms de classe de toutes les DLL dans l’espace de noms de l’application cliente a l’inconvénient que vous devez être prudent quels sont les ID ou noms que vous sélectionnez. Vous pouvez bien sûr désactiver cette fonctionnalité en ne pas d’exportation soit vos ressources ou une **CDynLinkLibrary** objet à l’application cliente. Le [DLLHUSK](../visual-cpp-samples.md) exemple gère l’espace de noms de ressource partagée à l’aide de plusieurs fichiers d’en-tête. Consultez [Note technique 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) pour plus d’informations sur l’utilisation de fichiers de ressources partagées.  
  
### <a name="initializing-the-dll"></a>L’initialisation de la DLL  
 Comme indiqué ci-dessus, vous souhaiterez généralement créer un **CDynLinkLibrary** objet afin d’exporter vos ressources et les classes à l’application cliente. Vous devez fournir un point d’entrée exporté pour initialiser la DLL. Au minimum, il s’agit d’une routine void qui n’accepte aucun argument et ne retourne rien, mais il peut s’agir comme vous le souhaitez.  
  
 Chaque application cliente afin de pouvoir utiliser votre DLL doive appeler cette routine d’initialisation, si vous utilisez cette approche. Vous pouvez également allouer cela **CDynLinkLibrary** de l’objet dans votre `DllMain` juste après l’appel `AfxInitExtensionModule`.  
  
 La routine d’initialisation doit créer un **CDynLinkLibrary** objet dans le segment de mémoire de l’application active, lié au vos informations de DLL d’extension MFC. Cela est possible avec les éléments suivants :  
  
```  
extern "C" extern void WINAPI InitXxxDLL()  
{  
    new CDynLinkLibrary(extensionDLL);

}  
```  
  
 Le nom de la routine, *InitXxxDLL* dans cet exemple, peut être comme vous le souhaitez. Il n’est pas nécessaire de `extern "C"`, mais rend ainsi plus facile à gérer la liste d’exportation.  
  
> [!NOTE]
>  Si vous utilisez votre DLL d’extension MFC à partir d’une DLL MFC standard, vous devez exporter cette fonction d’initialisation. Cette fonction doit être appelée à partir de la DLL MFC standard avant d’utiliser les classes DLL d’extension MFC ou les ressources.  
  
### <a name="exporting-entries"></a>Exportation des entrées  
 La simple pour exporter vos classes consiste à utiliser **__declspec (dllimport)** et **__declspec (dllexport)** sur chaque classe et de la fonction globale à exporter. Cela rend beaucoup plus facile, mais il est moins efficace que d’affectation de noms chaque point d’entrée (décrite ci-dessous), car vous avez moins de contrôle sur les fonctions qui sont exportées et vous ne pouvez pas exporter les fonctions par ordinal. TESTDLL1 et TESTDLL2 utilisent cette méthode pour exporter leurs entrées.  
  
 Une méthode plus efficace (et la méthode utilisée par MFCxx.DLL) consiste à exporter chaque entrée manuellement en nommant chaque entrée dans le. Fichier DEF. Étant donné que nous sommes exportation sélectives exportations à partir de notre DLL (autrement dit, pas tous les éléments), nous devons déterminer les interfaces particuliers, nous souhaitons à exporter. Cette opération est difficile, car vous devez spécifier les noms tronqués à l’éditeur de liens sous la forme d’entrées dans le. Fichier DEF. Ne d’exporter toutes les classes C++ sauf si vous souhaitez vraiment ont un lien symbolique pour celle-ci.  
  
 Si vous avez tenté d’exportation C++ classes avec une. Avant, vous pouvez souhaiter développer un outil pour générer automatiquement de cette liste de fichiers DEF. Cela est possible à l’aide d’un processus de liaison de deux étapes. Lier la DLL qu’une seule fois avec aucune exportation, et permettre à l’éditeur de liens générer un. Fichier de mappage. La barre d’outils. Fichier de mappage peut être utilisé pour générer une liste des fonctions qui doivent être exportées, avec certaines réorganisation, il peut être utilisé pour générer vos entrées d’exportation pour votre. Fichier DEF. La liste d’exportation pour MFCxx.DLL et OLE et les DLL d’extension MFC de base de données, plusieurs milliers de nombre, a été générée avec un tel processus (bien qu’il n’est pas entièrement automatique et requiert certains main paramétrage chaque fois dans un certain temps).  
  
### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary  
 Une DLL d’Extension MFC n’a pas un `CWinApp`-objet de son propre dérivé ; au lieu de cela, il doit fonctionner avec le `CWinApp`-dérivée de l’objet de l’application cliente. Cela signifie que l’application cliente possède la pompe de messages principale, la boucle inactive et ainsi de suite.  
  
 Si votre DLL d’Extension MFC doit gérer des données supplémentaires pour chaque application, vous pouvez dériver une classe nouvelle à partir de **CDynLinkLibrary** et la créer dans le InitXxxDLL routine décrites ci-dessus. Lors de l’exécution, la DLL peut consulter la liste de l’application en cours de **CDynLinkLibrary** objets à rechercher celui de cette DLL d’extension MFC particulière.  
  
### <a name="using-resources-in-your-dll-implementation"></a>Utilisation de ressources dans votre implémentation de DLL  
 Comme indiqué ci-dessus, la charge de ressources par défaut sera parcourent la liste des **CDynLinkLibrary** objets, recherchez le premier EXE ou DLL dans laquelle la ressource demandée. Toutes les API de MFC, ainsi que tout le code interne utilise `AfxFindResourceHandle` pour parcourir la liste des ressources pour rechercher n’importe quelle ressource, quel que soit l’où il peut résider.  
  
 Si vous souhaitez seulement charger les ressources à partir d’un emplacement spécifique, utilisez les API `AfxGetResourceHandle` et `AfxSetResourceHandle` pour enregistrer l’ancien handle et définir le nouveau handle. Veillez à restaurer l’ancien handle de ressource avant de retourner à l’application cliente. L’exemple TESTDLL2 utilise cette approche pour le chargement explicite d’un menu.  
  
 Parcourir la liste comporte les inconvénients qu’il est légèrement plus lente et nécessite la gestion de plages d’ID de ressource. Il a l’avantage qu’une application cliente qui est liée à plusieurs DLL d’extension MFC peut utiliser n’importe quelle ressource fournie par la DLL sans avoir à spécifier le handle d’instance DLL. `AfxFindResourceHandle` est une API utilisée pour parcourir la liste de ressources pour rechercher une correspondance donnée. Il prend le nom et le type d’une ressource et retourne le handle de ressource où elle a été trouvée en premier (ou NULL).  
  
##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Écrivez une Application qui utilise la Version DLL  
  
### <a name="application-requirements"></a>Exigences des applications  
 Une application qui utilise la version partagée de MFC doit suivre quelques règles simples :  
  
-   Il doit avoir un `CWinApp` de l’objet et de suivre les règles standards pour une pompe de messages.  
  
-   Il doit être compilé avec un ensemble d’indicateurs de compilateur requis (voir ci-dessous).  
  
-   Il doit lier avec les bibliothèques d’importation MFCxx. En définissant les indicateurs de compilateur requis, les en-têtes MFC déterminent au moment de la liaison de la bibliothèque dans laquelle l’application doit être liée à.  
  
-   Pour exécuter le fichier exécutable, MFCxx.DLL doit être sur le chemin d’accès ou dans le répertoire système Windows.  
  
### <a name="building-with-the-development-environment"></a>Création de l’environnement de développement  
 Si vous utilisez le fichier Make interne avec la plupart des valeurs par défaut standards, vous pouvez facilement modifier le projet pour générer la version de la DLL.  
  
 L’étape suivante suppose que vous possédez une application MFC fonctionne correctement liée avec NAFXCWD. LIB (pour le débogage) et NAFXCW. LIB (pour la vente au détail) et que vous souhaitez convertir pour utiliser la version partagée de la bibliothèque MFC. Vous exécutez l’environnement Visual C++ et que vous disposez d’un fichier de projet interne.  
  
1.  Sur le **projets** menu, cliquez sur **propriétés**. Dans le **général** page sous **projet par défaut est**, la valeur Microsoft Foundation Classes **utiliser les MFC dans une DLL partagée** (MFCxx(d).dll).  
  
### <a name="building-with-nmake"></a>Génération avec NMAKE  
 Si vous utilisez la fonctionnalité d’un makefile externe de Visual C++, ou utilisez NMAKE directement, vous devrez modifier votre fichier Make pour prendre en charge les options du compilateur et l’éditeur de liens  
  
 Indicateurs de compilateur requis :  
  
 **/ D_AFXDLL /MD**  
 **/ D_AFXDLL**  
  
 Les en-têtes MFC standards doivent ce symbole à définir :  
  
 **/MD**  
 L’application doit utiliser la version DLL de la bibliothèque Runtime C  
  
 Tous les autres indicateurs de compilateur suivent les valeurs par défaut MFC (par exemple, _DEBUG pour le débogage).  
  
 Modifier la liste de l’éditeur de liens des bibliothèques. Modification NAFXCWD. LIB à MFCxxD.LIB et modifier NAFXCW. LIB à MFCxx.LIB. Remplacez LIBC. LIB avec MSVCRT. LIB. Comme avec toute autre bibliothèque MFC, il est important que MFCxxD.LIB est placé **avant** toutes les bibliothèques runtime C.  
  
 Ajoutez éventuellement **/D_AFXDLL** pour votre vente au détail et débogage options du compilateur de ressources (celui qui a réellement compile les ressources avec **/R**). Cela rend votre exécutable final plus petits en partageant les ressources qui sont présents dans la DLL MFC.  
  
 Une régénération complète est requise après que ces modifications sont apportées.  
  
### <a name="building-the-samples"></a>Génération des exemples  
 La plupart des exemples de programmes MFC peut être construite à partir de Visual C++ ou d’un MAKEFILE NMAKE compatibles partagé à partir de la ligne de commande.  
  
 Pour convertir un de ces exemples à utiliser MFCxx.DLL, vous pouvez charger le. Clé MAK fichier dans Visual C++ et définir les options de projet comme décrit ci-dessus. Si vous utilisez la génération NMAKE, vous pouvez spécifier « AFXDLL = 1 » sur le NMAKE ligne de commande et qui générera l’exemple en utilisant les bibliothèques MFC partagées.  
  
 L’exemple MFC Advanced Concepts [DLLHUSK](../visual-cpp-samples.md) est généré avec la version DLL de MFC. Cet exemple illustre non seulement la création d’une application liée avec MFCxx.DLL, mais il illustre également les autres fonctionnalités de l’option d’empaquetage de DLL MFC telles que des DLL d’Extension MFC décrite plus loin dans cette note technique.  
  
### <a name="packaging-notes"></a>Notes de mise en package  
 La version commerciale des DLL (MFCxx [U]. DLL) peuvent être redistribuées librement. La version debug des DLL ne sont pas redistribuable librement et doit être utilisé uniquement pendant le développement de votre application.  
  
 La DLL de débogage sont fournies avec les informations de débogage. À l’aide du débogueur Visual C++, vous pouvez tracer l’exécution de votre application, ainsi que la DLL. Les DLL de version (MFCxx [U]. DLL) ne contiennent pas les informations de débogage.  
  
 Si vous personnalisez ou régénérez les DLL, puis vous devez appeler les quelque chose que le fichier « MFCxx » le MFC SRC MFCDLL. Clé MAK décrit les options de build et contient la logique pour la modification du nom de la DLL. Renommer les fichiers n’est nécessaire, étant donné que ces DLL est potentiellement partagés par de nombreuses applications MFC. Avec votre version personnalisée de la DLL MFC de remplacer celles installées sur le système peuvent interrompre une autre application MFC à l’aide de la DLL MFC partagée.  
  
 La reconstruction de la DLL de MFC n’est pas recommandée.  
  
##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> L’implémentation MFCxx.DLL  
 La section suivante décrit comment la DLL MFC (MFCxx.DLL et MFCxxD.DLL) est implémentée. Comprendre que les détails ici sont également pas important si vous souhaitez effectuer est d’utiliser la DLL MFC avec votre application. Les détails ici ne sont pas indispensables pour comprendre comment écrire une DLL d’extension MFC, mais la présentation de cette implémentation peut vous aider à écrire votre propre DLL.  
  
### <a name="implementation-overview"></a>Vue d’ensemble de l’implémentation  
 La DLL MFC est réellement un cas spécial d’une DLL d’Extension MFC comme décrit ci-dessus. Il possède un très grand nombre d’exportations pour un grand nombre de classes. Il existe quelques éléments supplémentaires que nous le faisons dans la DLL MFC qui le rendent plus spéciaux à une DLL d’extension MFC standard.  
  
### <a name="win32-does-most-of-the-work"></a>Win32 exécute la plupart des travaux  
 La version 16 bits de MFC nécessaire à un nombre de techniques spécifiques, y compris les données par application sur le segment de la pile, des segments spéciaux créés par du code de l’assembly de 80 x 86, par processus exception contextes et autres techniques. Win32 prend directement en charge les données par processus dans une DLL, qui est ce que vous souhaitez la plupart du temps. La plupart du temps MFCxx.DLL est simplement NAFXCW. LIB empaquetée dans une DLL. Si vous examinez le code source MFC, vous trouverez très peu #ifdef _AFXDLL, car il existe quelques cas spéciaux qui doivent être apportées. Les cas spéciaux existe spécifiquement pour gérer Win32 3.1 de Windows (également appelée Win32s). Win32s ne pas les données DLL par processus prise en charge directement la DLL MFC doivent utiliser le stockage local des threads (TLS), les API Win32 pour obtenir des données locales de processus.  
  
### <a name="impact-on-library-sources-additional-files"></a>Impact sur les fichiers supplémentaires à la source de la bibliothèque  
 L’impact de la **_AFXDLL** version dans les en-têtes et les sources de bibliothèque de classe MFC normale est mineure. Il existe un fichier de version spéciale (AFXV_DLL. (H), ainsi qu’un fichier d’en-tête supplémentaires (AFXDLL_. H) inclus par le principal AFXWIN. En-tête de H. Le AFXDLL_. H en-tête comprend le **CDynLinkLibrary** classe et autres détails d’implémentation des deux **_AFXDLL** applications et des DLL d’Extension MFC. Le AFXDLLX. En-tête de H est fourni pour la création de DLL d’Extension MFC (voir ci-dessus pour plus d’informations).  
  
 Les sources régulières à la bibliothèque MFC dans MFC SRC ont du code conditionnel supplémentaire sous les **_AFXDLL** #ifdef. Un fichier source supplémentaire (DLLINIT. CPP) contient le code d’initialisation de DLL supplémentaire et autres collage de la version partagée de MFC.  
  
 Pour générer la version partagée de MFC, les fichiers supplémentaires sont fournies. (Voir ci-dessous pour plus d’informations sur la création de la DLL).  
  
-   Deux. Fichiers DEF sont utilisés pour l’exportation les points d’entrée DLL MFC pour le débogage (MFCxxD.DEF) et (MFCxx.DEF) version finale de la DLL.  
  
-   Une barre d’outils. Fichier RC (MFCDLL. RC) contient toutes les ressources MFC standards et une ressource VERSIONINFO pour la DLL.  
  
-   UN FICHIER. Fichier CLW (MFCDLL. CLW) est fourni pour permettre la navigation de la bibliothèque MFC, classes à l’aide de ClassWizard. Remarque : cette fonctionnalité n’est pas spécifique à la version DLL de MFC.  
  
### <a name="memory-management"></a>Gestion de la mémoire  
 Une application à l’aide de MFCxx.DLL utilise un allocateur de mémoire commune fourni par MSVCRTxx.DLL, la DLL partagée runtime C. L’application, toutes les DLL d’extension MFC et ainsi que les DLL MFC elles-mêmes utilisent cet allocateur de mémoire partagée. En utilisant une DLL partagée pour l’allocation de mémoire, les DLL MFC peuvent allouer la mémoire libérée ultérieurement par l’application, ou vice versa. Étant donné que l’application et la DLL doivent utiliser l’allocateur de même, vous ne devez pas remplacer le C++ global `operator new` ou `operator delete`. Les mêmes règles s’appliquent au reste des routines d’allocation de mémoire du runtime C (tel que `malloc`, `realloc`, **libre**, etc.).  
  
### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Les ordinaux et classe __declspec (dllexport) et les DLL d’affectation de noms  
 Nous n’utilisons pas la `class` **__declspec (dllexport)** fonctionnalités du compilateur C++. Au lieu de cela, une liste d’exportations est incluse dans la source de bibliothèque de classes (MFCxx.DEF et MFCxxD.DEF). Seulement sélectionnez ensemble de points d’entrée (fonctions et données) sont exportés. Autres symboles tels que des fonctions MFC implémentation privée ou des classes, ne sont pas exportés toutes les exportations sont effectuées par ordinal sans un nom de chaîne dans la table de noms résident ou non résident.  
  
 À l’aide de `class` **__declspec (dllexport)** peut être une alternative viable pour la création d’une DLL plus petite, mais dans le cas d’une DLL volumineuse tels que MFC, la valeur par défaut exportation mécanisme a l’efficacité et la capacité de limites.  
  
 Cela signifie que toutes les nouveautés que nous pouvons package une grande quantité de fonctionnalités de la version MFCxx.DLL est uniquement environ 800 Ko sans compromettre la quantité d’exécution ou la vitesse de chargement. MFCxx.DLL aurait été supérieure à 100 Ko avait cette technique pas été utilisé. Cela rend également possible d’ajouter des points d’entrée supplémentaires à la fin de le. Fichier DEF pour permettre le contrôle de version simple sans compromettre l’efficacité de vitesse et la taille de l’exportation par ordinal. Les révisions de version principale de la bibliothèque de classe MFC modifie le nom de la bibliothèque. Autrement dit, MFC30. DLL est la DLL redistribuable contenant la version 3.0 de la bibliothèque de classes MFC. Une mise à niveau de cette DLL, par exemple, dans un hypothétique 3.1 de MFC, la DLL serait nommée MFC31. DLL à la place. Là encore, si vous modifiez le code source MFC pour produire une version personnalisée de la DLL de MFC, utilisez un autre nom (et, de préférence, sans « MFC » dans le nom).  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

