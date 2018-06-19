---
title: 'TN058 : Implémentation de l’état du Module MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.implementation
dev_langs:
- C++
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90e407299f67922aa855a51b9983af074cdbd4fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385750"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058 : implémentation de l'état du module MFC
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note technique décrit l’implémentation de constructions de « État du module MFC ». Est de comprendre l’implémentation du module état critique pour à l’aide de la bibliothèque MFC des DLL à partir d’une DLL partagées (ou un serveur in-process OLE).  
  
 Avant de lire cette note, consultez « Gestion les données d’état des Modules MFC » dans [création de nouveaux Documents, fenêtres et de vues](../mfc/creating-new-documents-windows-and-views.md). Cet article contient des informations importantes sur l’utilisation et des informations générales sur ce sujet.  
  
## <a name="overview"></a>Vue d'ensemble  
 Il existe trois types d’informations d’état MFC : état du Module, l’état du processus et l’état du Thread. Parfois, ces types d’état peuvent être combinées. Par exemple, les cartes de handles de MFC sont module local et thread local. Ainsi, les deux modules différents avoir des mappages différents dans chacun de leurs threads.  
  
 État du processus et l’état du Thread sont similaires. Ces éléments de données sont traditionnellement les variables globales, mais être amené à être spécifiques à un processus donné ou thread pour la prise en charge Win32s approprié, ou pour la prise en charge du multithreading approprié. Catégorie à laquelle un élément de données donnée rentre dans dépend de cet élément et ses sémantiques souhaitées en matière de limites de processus et de thread.  
  
 État du module est unique car elle peut contenir le véritablement globale état ou qui est le processus local ou thread local. En outre, il est possible de rapidement.  
  
## <a name="module-state-switching"></a>Changement d’état du module  
 Chaque thread contient un pointeur vers l’état du module « Active » ou « actifs » (sans surprise, le pointeur fait partie d’état local de thread de MFC). Ce pointeur est modifié lorsque le thread d’exécution passe la limite d’un module, tel qu’une application dans un contrôle OLE ou DLL ou un contrôle OLE rappel dans une application.  
  
 L’état du module en cours est basculée en appelant **AfxSetModuleState**. Dans la plupart des cas, vous gérerez jamais directement avec l’API. MFC, dans de nombreux cas, il vous demandera (à WinMain, OLE-points d’entrée, **AfxWndProc**, etc..). Cette opération est effectuée dans n’importe quel composant que vous écrivez en la liant statiquement dans une spéciale **WndProc**et une spéciale `WinMain` (ou `DllMain`) qui sait quel état de module doit être en cours. Vous pouvez voir ce code en examinant DLLMODUL. RPC ou APPMODUL. CPP dans le répertoire MFC\SRC.  
  
 Il est rare que vous souhaitez définir l’état du module et donnez-lui la valeur de retour pas. La plupart du temps que vous souhaitez « push » votre propre module d’état que celui en cours et ensuite, une fois que vous avez terminé, « pop » dans un contexte d’origine. Pour cela, la macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) et la classe spéciale **AFX_MAINTAIN_STATE**.  
  
 `CCmdTarget` possède des fonctionnalités spéciales pour prendre en charge le changement d’état module. En particulier, un `CCmdTarget` est la classe racine utilisée pour OLE automation et OLE COM points d’entrée. Comme n’importe quel autre point d’entrée exposés au système, ces points d’entrée doivent définir l’état du module approprié. Comment est une donnée `CCmdTarget` savoir ce que l’état du module « correct » doit être la réponse est qu’il « souvient de « quel est l’état du module « active » lorsqu’il est construit, tel qu’il peut définir l’état du module en cours pour que « mémorisés » appelé de valeur lorsqu’il est plus loin. Par conséquent, le module d’état qui une donnée `CCmdTarget` est associé l’objet est l’état du module qui était actuelle lorsque l’objet a été construit. Prendre un exemple simple de chargement d’un serveur INPROC, création d’un objet et appeler ses méthodes.  
  
1.  La DLL est chargée par OLE à l’aide de **LoadLibrary**.  
  
2. **RawDllMain fournie** est appelée en premier. Il définit l’état du module à l’état du module statique connu pour la DLL. Pour cette raison **RawDllMain fournie** statiquement liée à la DLL.  
  
3.  Le constructeur de la fabrique de classe associé à notre objet est appelé. `COleObjectFactory` est dérivé de `CCmdTarget` et par conséquent, il souvient dans quel état de module, il a été instancié. Ceci est important, lorsque la fabrique de classe est invitée à créer des objets, il sait maintenant l’état du module pour rendre actuel.  
  
4. `DllGetClassObject` est appelé pour obtenir la fabrique de classe. MFC recherche dans la liste de fabrique de classe associée à ce module et le retourne.  
  
5. **COleObjectFactory::XClassFactory2::CreateInstance** est appelée. Avant la création de l’objet et de la renvoyer, cette fonction affecte l’état du module à l’état du module en cours à l’étape 3 (celle qui était actuelle lorsque le `COleObjectFactory` a été instancié). Cette opération est effectuée à l’intérieur de [METHOD_PROLOGUE](com-interface-entry-points.md).  
  
6.  Lorsque l’objet est créé, il est trop un `CCmdTarget` dérivés et de la même façon `COleObjectFactory` mémorisés quel état module était actif, c’est ce nouvel objet. À présent l’objet sait quel état de module pour basculer vers chaque fois qu’elle est appelée.  
  
7.  Le client appelle une fonction sur l’objet OLE COM qu’il a reçu à partir de son `CoCreateInstance` appeler. Lorsque l’objet est appelée, elle utilise `METHOD_PROLOGUE` pour basculer l’état du module comme `COleObjectFactory` est.  
  
 Comme vous pouvez le voir, l’état du module est propagée à partir de l’objet à l’objet comme elles sont créées. Il est important d’avoir l’état du module définie de manière appropriée. Si elle n’est pas définie, l’objet de la DLL ou COM peut interagir mal avec une application MFC qui l’appelle, ou peut être impossible de trouver ses propres ressources ou peut échouer dans d’autres façons d’effectuer.  
  
 Notez que certains types de DLL, en particulier les DLL « Extension MFC » ne change pas l’état du module dans leurs **RawDllMain fournie** (en fait, ils généralement n’ont pas un **RawDllMain fournie**). Il s’agit, car ils sont conçus pour se comporter « comme si « elles étaient réellement présents dans l’application qui les utilise. Ils sont très bien une partie de l’application est en cours d’exécution et il s’agit de son intention de modifier l’état global de l’application.  
  
 Contrôles OLE et autres DLL est très différents. Ils ne souhaitent pas modifier l’état de l’application appelante ; l’application qui les appelle même peut-être pas une application MFC et par conséquent, il ne peut y avoir aucun état à modifier. Il s’agit de la raison que le changement d’état module a été inventé.  
  
 Pour des fonctions exportées à partir d’une DLL, tel que celui qui lance une boîte de dialogue dans votre DLL, vous devez ajouter le code suivant au début de la fonction :  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState())  
```  
  
 Cela permute l’état du module en cours avec l’état retourné à partir de [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) jusqu'à la fin de la portée actuelle.  
  
 Les problèmes avec des ressources dans les DLL se poseront si la macro `AFX_MODULE_STATE` n'est pas utilisée. Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Ce modèle est réellement enregistré dans la DLL. La cause première est que les informations d'état du module MFC n'ont pas été basculées par la macro `AFX_MODULE_STATE`. Le handle de ressources est récupéré de l'état du module MFC. Ne pas afficher l'état du module provoque l'utilisation du mauvais handle de ressource.  
  
 `AFX_MODULE_STATE` n’a pas besoin à placer dans chaque fonction dans la DLL. Par exemple, `InitInstance` peut être appelé par du code MFC dans l'application sans `AFX_MODULE_STATE` car MFC déplace automatiquement l'état du module avant `InitInstance`, puis le restaure après le retour de `InitInstance`. Cela vaut également pour tous les gestionnaires de mappage de message. Les DLL régulières MFC ont une procédure de fenêtre principale spéciale qui bascule automatiquement l’état du module avant d’acheminer un message.  
  
## <a name="process-local-data"></a>Traitement des données locales  
 Traiter les données locales ne sont pas que de telles préoccupation n'avait pas été pour la difficulté du modèle Win32s DLL. Dans Win32s toutes les DLL partagent leurs données globales, même lorsque le chargement par plusieurs applications. Cela est très différent du modèle de données de DLL Win32 « real », où chaque DLL Obtient une copie distincte de son espace de données dans chaque processus qui s’attache à la DLL. Pour ajouter à la complexité, données allouées sur le tas dans une DLL Win32s sont en fait les processus spécifiques (au moins autant que la propriété est). Tenez compte des données et au code suivant :  
  
```  
static CString strGlobal; // at file scope  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz,
    size_t cb)  
{  
    StringCbCopy(lpsz,
    cb,
    strGlobal);

}  
```  
  
 Considérez que se passe-t-il si le code ci-dessus dans se trouve dans une DLL et que la DLL est chargée par deux processus A et B (il peut être en fait, deux instances de la même application). Un appel `SetGlobalString("Hello from A")`. Par conséquent, la mémoire est allouée pour le `CString` les données dans le contexte du processus A. Gardez à l’esprit que le `CString` lui-même est global et est visible pour les deux A et b. Maintenant B appelle `GetGlobalString(sz, sizeof(sz))`. B sera en mesure de voir les données ensemble. Il s’agit, car Win32s n’offre aucune protection entre les processus comme Win32. Qui est le premier problème ; dans de nombreux cas, il n’est pas souhaitable de disposer d’une application affecte les données globales sont considéré comme appartenant à une autre application.  
  
 Il existe des problèmes supplémentaires. Supposons que maintenant se termine. Lorsque A se termine, la mémoire utilisée par la '`strGlobal`' chaîne devient disponible pour le système, autrement dit, toute la mémoire allouée par le processus A est libérée automatiquement par le système d’exploitation. Il n’est pas libéré, car le `CString` destructeur est appelé ; il n’a pas encore été appelée. Elle est libérée simplement parce que l’application qui lui a été alloué a quitté la scène. Maintenant, si elle est appelée de B `GetGlobalString(sz, sizeof(sz))`, il ne disposeront pas de données valide. D’autres applications peuvent avoir utilisé que la mémoire pour autre chose.  
  
 Clairement un problème existe. MFC 3.x utilisé une technique appelée le stockage local des threads (TLS). MFC 3.x affecte un index TLS qui sous Win32s agit comme un index de stockage local des processus, même si elle n’est pas appelée qu’et serait faire référence à toutes les données en fonction de cet index TLS. Ceci est similaire à l’index TLS qui a été utilisé pour stocker des données locales de thread sur Win32 (voir ci-dessous pour plus d’informations sur le sujet). Cela a provoqué chaque DLL MFC à utiliser au moins deux des indices TLS par processus. Lorsque vous prendre en compte pour le chargement de contrôle DLL OLE (OCX), vous manquer rapidement les indices TLS (64 uniquement sont disponibles). En outre, MFC devait placer toutes ces données dans un seul endroit, dans une structure unique. Il n’était pas très extensible et n’est pas idéale en ce qui concerne l’utilisation d’indices TLS.  
  
 MFC 4.x de préciser ce point avec un ensemble de modèles de classe que vous pouvez « enveloppé » les données qui doivent être des processus locaux. Par exemple, le problème mentionné ci-dessus peut être résolu en écrivant :  
  
```  
struct CMyGlobalData : public CNoTrackObject  
{  
    CString strGlobal;  
};  
CProcessLocal<CMyGlobalData> globalData;  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    globalData->strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz, size_t cb)  
{  
    StringCbCopy(lpsz, cb, globalData->strGlobal);

}  
```  
  
 MFC implémente ce en deux étapes. Tout d’abord, est une couche sur Win32 **Tls\***  API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc.) qui Utilisez uniquement deux index TLS par processus, quel que soit le nombre de DLL que vous avez. Ensuite, le `CProcessLocal` modèle est fourni pour accéder à ces données. Il substitue l’opérateur -> qui est ce qui permet la syntaxe intuitive affichés ci-dessus. Tous les objets qui sont encapsulés par `CProcessLocal` doit être dérivé de `CNoTrackObject`. `CNoTrackObject` fournit un allocateur de niveau inférieur (**LocalAlloc**/**LocalFree**) et un destructeur virtuel telles que MFC peut détruire automatiquement les objets locaux de processus lorsque le processus est terminé. Ces objets peuvent avoir un destructeur personnalisé si un nettoyage supplémentaire est nécessaire. L’exemple ci-dessus ne nécessite pas un, étant donné que le compilateur génère un destructeur par défaut pour détruire l’embedded `CString` objet.  
  
 Il existe des autres avantages intéressantes de cette approche. Sont non seulement toutes les `CProcessLocal` objets détruits automatiquement, elles sont construites pas jusqu'à ce qu’ils sont nécessaires. `CProcessLocal::operator->` instancie l’objet associé à la première fois qu’elle est appelée et aucune plus tôt. Dans l’exemple ci-dessus, cela signifie que le «`strGlobal`' chaîne ne sera construite jusqu'à ce que la première fois **SetGlobalString** ou **GetGlobalString** est appelée. Dans certains cas, cela peut aider à réduire le temps de démarrage DLL.  
  
## <a name="thread-local-data"></a>Données locales de thread  
 Comme pour traiter les données locales, les données locales de thread sont utilisées lorsque les données doivent être locales sur un thread donné. Autrement dit, vous devez une instance distincte des données pour chaque thread qui accède à ces données. Ce nombre de fois où permet à la place des mécanismes de synchronisation complète. Si les données ne doivent pas être partagée par plusieurs threads, ces mécanismes peuvent être coûteuse et inutiles. Supposons que nous avons eu un `CString` objet (semblable à l’exemple ci-dessus). Nous pouvons rendre thread local en encapsulant avec un `CThreadLocal` modèle :  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
    CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
 
void MakeRandomString()  
{ *// a kind of card shuffle (not a great one)  
    CString& str = threadData->strThread;  
    str.Empty();
while (str.GetLength() != 52)  
 {  
    unsigned int randomNumber;  
    errno_t randErr;  
    randErr = rand_s(&randomNumber);

    if (randErr == 0)  
 {  
    TCHAR ch = randomNumber % 52 + 1;  
    if (str.Find(ch) <0)  
    str += ch; // not found, add it  
 }  
 }  
}  
```  
  
 Si `MakeRandomString` a été appelée à partir de deux threads différents, chacun serait « aléatoire » la chaîne de différentes manières sans interférer avec les autres. Il s’agit, car il est en fait un `strThread` instance par thread au lieu d’une instance globale.  
  
 Notez la façon dont une référence est utilisée pour capturer le `CString` adresse, une seule fois plutôt qu’une seule fois par itération de boucle. Le code de la boucle ont été écrits avec `threadData->strThread` everywhere '`str`' est utilisé, mais le code serait beaucoup plus lent dans l’exécution. Il est préférable de mettre en cache une référence aux données en cas de telles références dans les boucles.  
  
 Le `CThreadLocal` modèle de classe utilise les mêmes mécanismes que `CProcessLocal` n’a et les mêmes techniques d’implémentation.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

