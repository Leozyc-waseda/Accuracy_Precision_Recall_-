# Accuracy_Precision_Recall_-



关于A,P,R常用的说明


首先，这几个指标都是分类器的评价标准，分类(Classification)是机器学习中需要解决的主要问题之一。要想了解这几个分类器评价标准的优缺点，首先我们从问题定义出发。


# 何为分类？
简而言之，就是根据已有的特征数据，对预测值进行分类。

举三个例子，为了方便，例子都是二分类(Binary Classification)问题。

1. 我想做一个好玩的软件，通过输入人的各种特征，判断这个人是喜欢猫还是喜欢狗。

那么我可能会去搜集测试者的性别，职业，星座，性格特征等等对测试者的猫狗偏好

进行预测。这里的分类是：喜欢猫/喜欢狗。

2. 银行通过所拥有的贷款人信息，去对贷款人是否会违约不还款进行预测。这里银行所拥有的贷款人信息，

例如贷款人的性别，职业，收入，学历，房产等等数据就是特征，而银行需要用这些数据进行的分类是：违约/不违约。

3. 某大型流行传染病爆发，检疫局对所有检测者进行疑似诊断。这里检疫局搜集到的人体检测数据，

例如性别，年龄，体温，患病体征等数据是特征，而需要用这些数据进

行分类：患病/未患病。

既然有预测，并且有真实值，那么我们就有基于预测值与真实值两个属性的四种状态。

1. 预测值为正(Positive)，并且真实值也为正(Positive)，预测为真(True)，True Positive (TP)。

2. 预测值为负(Negative)，但是真实值为正(Positive)，预测失败(False)，False Negative (FN)。

3. 预测值为正(Positive)，但是真实值为负(Negative)，预测失败(False)，False Positive (FP)。

4. 预测值为负(Negative)，并且真实值也为负(Negative)，预测为真(True)，True Negative (TN)。


![image](https://github.com/Leozyc-waseda/Accuracy_Precision_Recall_-/blob/master/image/1.png)


这个矩阵就是著名的混淆矩阵(Confusion Matrix)，可能是因为各种比例计算比较复杂，所以被这样命名。为了更好地表示清楚，我这里尽可能对不同类别做了区分：


![image](https://github.com/Leozyc-waseda/Accuracy_Precision_Recall_-/blob/master/image/2.png)


这里的正负，其实不是真实的某个正负，一般的做法是将需要检测的异常行为设置为正(Positive)，而将不存在目标行为设置为负(Negative)。

在银行预测用户是否违约的例子中，因为我们关注的是客户是否会违约，以提前防范客户违约，所以违约就是正(Positive)，而不违约就是负(Negative)。

#定义了问题，并且有了具体的例子，我们可以回到这个问题本身。


# 准确率(Accuracy)

既然我们是做预测，那自然希望我们做出的预测尽可能的准确，准确率就是在所有样本数中，我们做出正确预测(True)的样本比例。在图中就是

![image](https://github.com/Leozyc-waseda/Accuracy_Precision_Recall_-/blob/master/image/3.png)

准确率(Accuracy)的适用场景：

不同的分类是同等地位的，例如在例子1中，对猫狗洗好进行分类，问题中并没有对猫和狗有特定的侧重，因此在这里我们只强调于分类的正确度，即准确率。

# 精确率(Precision)


但更一般的分类问题，对于类别往往有所侧重，例如银行进行用户违约预测的例子中，

银行更关注的是那些少量的违约案例，因为这关系到贷出资金能否收回，涉及坏账率，因此需要一个针对于正预测(Positive)的指标，

所以这里银行会更加看重所做出的正预测中，预测为真(True)的比例。

![image](https://github.com/Leozyc-waseda/Accuracy_Precision_Recall_-/blob/master/image/4.png)

精确率(Precision)的适用场景：

因为预测为正但真实为负(FP)的成本很高，因此非常看重预测正样本预测的准确度。

比如在银行对用户违约与否进行预测时，假如将客户分类为会违约，但客户实际不违约，那么银行损失了一名客户，同时也损失了利息收入，

所以银行会比较看重预测的精确度。


# 召回率(Recall)

召回率又可以被翻译为查全率，同样基于对于正(Positive)案例的指标。

但与精确率不同之处在于，召回率更加侧重真实为正(Positive)的样本中被成功预测的比例。

![image](https://github.com/Leozyc-waseda/Accuracy_Precision_Recall_-/blob/master/image/5.png)


召回率(Recall)的适用场景：
在真实值为正，而未被成功预测为正(FN)的成本很高，因此非常看重真实为正样本被正确预测的比例。比如在流行病的案例中，如果真实为正而未被正确预测，即本身患病而被判断为不患病，那么对于社会公共安全造成极大危害，后果严重，所以这里会很看重召回率。




