#  单链表

- **单链表**:链表为空，下个节点为NULL
- 数据，节点：数据域 指针域指向下个节点，
- 链表创建
- 头插法 尾插法
- 删除节
- 遍历链表

#### 创建链表

~~~c
typedef struct Node
{
	int data;
	struct Node* next;
}Node;//节点

Node* initlist()
{
	Node* list = (Node*)calloc(1, sizeof(Node));
	return list;
}//头结点
//链表以创建
~~~

#### 头插法

~~~c
void headinsert(Node* list, int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;//创建新节点并插入数据

	node->next = list->next;
	list->next = node;
}
~~~

#### 尾插法

~~~c
//尾插法
void tailinsert(Node* list,int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;
	node->next = NULL;//尾节点下个节点为空


	//找到下个节点为空节点
	while (list->next) list=list->next;
	list->next = node;
}

~~~

#### 删除节点

**删除操作**：要删除的节点的上个节点，指向要删除节点的下个节点。所以要记录删除节点以方便上节点指向删除节 点的下个节点。还要记录删除节点的上个节点

~~~c
int deletelist(Node* list, int data)
{
	Node* dellist = list->next;//要删除的节点
	while (dellist)
	{
		if (dellist->data == data)
		{
			list->next = dellist->next;
			free(dellist);
			dellist = NULL;
			return 1;
		}
		list = list->next;//移动删除节点的上个节点
		dellist = dellist->next;//移动删除
	}
	return 0;
}
~~~

#### 链表的遍历

~~~c
//遍历
void printlist(Node* list)
{
	while (list = list->next)
	{
		printf("%d->", list->data);
	}
	printf("NULL\n");
}
~~~

# 双链表

* 双链表:多个指针域指向上个节点

* 头插法 尾插法 删除节点 遍历

#### 创建链表

~~~c
typedef struct Node
{
	int data;
	struct Node* pre;
	struct Node* next;
}Node;

Node* initlist()
{
	Node* list = (Node*)calloc(1, sizeof(Node));
	return list;
}//双链表的创建
~~~

#### 头插法

~~~c
void headinesert(Node* list, int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;

	if (list->next == NULL)
	{
		//如果空链表，头节点的下个节点的pre不在指向
		node->next = list->next;
		node->pre = list;
		list->next = node;
	}
	else
	{
		node->next = list->next;
		node->pre = list;
		list->next->pre = node;
		list->next = node;
	}
}
~~~

#### 尾插法

~~~c
void tailinesert(Node* list, int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;
	node->next = NULL;

	while (list->next) list = list->next;
	list->next = node;
	node->pre = list;
}
~~~

#### 删除节点

~~~c
int deletelist(Node* list, int data)
{
	//因为有pre的存在，不需要记录要删除节点的上个节点
	Node* delnode = list->next;//要删除的节点

	while (delnode)
	{
		if (delnode->data == data)
		{
			delnode->pre->next = delnode->next;

			//如果要删除的节点的下个节点为空pre不在指向上节点
			if (delnode->next != NULL)
			{
				delnode->next->pre = delnode->pre;
			}
			free(delnode);
			delnode = NULL;
			return 1;
		}
		//移动要删除的节点
		delnode = delnode->next;
	}
	return 0;
}
~~~

# 单循环链表

* **单循环链表**:链表为空，下个节点指向头节点的地址
* 头插法 尾插法 删除节点 遍历

#### 头插法

~~~c
//头插法
void headinsert(Node* list, int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;

	node->next = list->next;
	list->next = node;
}
~~~

#### 尾插法

~~~c
//尾插法
void tailinsert(Node* list, int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;
	node->next = list;

	//如果下个节点是头节点的地址
	//就是尾节点,要保存头节点的地址
	Node* pre = list;
	while (pre->next != list) pre = pre->next;
	pre->next = node;
}
~~~

#### 删除节点

~~~c
//删除节点
int deletelist(Node* list, int data)
{
	Node* delnode = list->next;
	while (delnode != list)
	{
		if (delnode->data == data)
		{
			list->next = delnode->next;
			free(delnode);
			delnode = NULL;
			return 1;
		}
		list = list->next;
		delnode = delnode->next;
	}
	return 0;
}
~~~

#### 遍历链表

~~~c
void printlist(Node* list)
{
	Node* pre = list;
	while ((pre = pre->next) != list)
	{
		printf("%d->", pre->data);
	}
	printf("%d", list->data);
}
~~~

# 双循环链表

* 双循环链表:链表为空下个节点指向头节点，pre指向头节点
* 头插法，尾插法，删除节点，遍历

#### 创建链表

~~~c
typedef struct Node
{
	int data;
	struct Node* pre;
	struct Node* next;
}Node;//节点

Node* initlist()
{
	Node* list = (Node*)calloc(1, sizeof(Node));
	list->data = 713;
	list->next = list;
	list->pre = list;
	return list;
}//头节点
~~~

#### 头插法

~~~c
//头插法
void headinsert(Node* list, int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;

	if (list->next == list)
	{
		//list的下节点为不必操作pre
		node->next = list->next;
		node->pre = list;
		list->next = node;
	}
	else
	{
		node->next = list->next;
		node->pre = list;
		list->next->pre = node;
		list->next = node;
	}
}
~~~

#### 尾插法

~~~c
//尾插法
void tailinsert(Node* list, int data)
{
	Node* node = (Node*)malloc(sizeof(Node));
	node->data = data;
	node->next = list;
	
	Node* pre = list;
	while (pre->next != list) pre = pre->next;
	pre->next = node;
	node->pre = pre;
}
~~~

#### 删除节点

~~~c
//删除节点
int deletelist(Node* list, int data)
{
	Node* delnode = list->next;

	while (delnode != list)
	{
		if (delnode->data == data)
		{
			delnode->pre->next = delnode->next;
			//如果下个节点不是空执行pre
			if (delnode->next != list)
				delnode->next->pre = delnode->pre;
			free(delnode);
			delnode = NULL;
			return 1;
		}
		delnode = delnode->next;
	}
	return 0;
}

~~~

#### 遍历

~~~c
//遍历
void printlist(Node* list)
{
	Node* movenode = list;
	while ((movenode = movenode->next) != list)
	{
		printf("%d->", movenode->data);
	}
	printf("%d", movenode->data);
}
~~~

### 字符串mkp匹配

~~~c
//a b a a b c a c
j=-1 i=0

if (j == -1 || s->data[i] == s->data[j])
{
	i++, j++;
	next[i] = j;
}
else
{
    //2：j=-1
	j = next[j]; 
}
~~~

next[0]=-1	next[1]=0	next[2]=0	next[3]=1	next[4]	next[5]	next[6]	next[7]



















