开场

分为四个模块

我所负责的职责与产出 收获与新的、未来学习计划 加入团队的感受 对导师和团队的反馈和建议

1. 我所负责的职责与产出

   我的岗位是前端开发，在实习期间，我主要参与的项目是客户侧的在线客服和工单系统灰度入口的开发。

   在线客服 
   - 简介

     在线客服项目主要是为客户提供了一个自助解决问题的渠道，首先用户可以通过智能客服获取相关问题的回答，如果智能客服的回答无法帮助用户解决问题，则可以通过接入人工客服或提交工单来解决问题，同时会有右侧的自助工具以及快捷入口来帮助客户更好的自助解决问题

   - 功能
      - 富文本框编辑

        比起老版的智能客服，新版的在线客服由于接入人工客服的需要，客户需要更丰富的沟通的表达方式，因此有了支持文件、图片以及表情的富文本框支持

        富文本框的编辑功能一直以来都是前端的做起来比较有困难的点，

        1. 对于当今主流前端框架，无论是vue还是react，都是提倡以数据驱动视图类MVVM的框架，不去主动操作视图，而是通过操作数据渲染视图。但是富文本框则不一样，需要我们直接对html dom节点做很多操作，让我们一下子回到了五年前用没有mvvm框架，直接操作dom节点的编程方式。

        2. 此外，对于某些dom节点的api，在不同浏览器上也会存在一定的兼容性问题，需要我们手动编写方法兼容；

        3. 而且由于本次实现中，受到设计的限制我们也无法采用其他外部的解决方案，所以我们这个富文本框，可以说是从一个div开始实现到一个支持编辑各种文件富文本的。

        后续考虑其他地方复用，我也正在把他抽离出来可能是作为我们的一个自己开发的包或组件，方便在其他地方使用

      - 消息记录

        消息记录是在每次接入人工会话结束后，会产生一条消息记录，记录客服和客户两端的所有对话信息，方便客户查找历史消息

        在初期，我们对下拉列表以及右边的内容部分都采用了懒加载方式加载消息，以防单次加载数据量过大导致明显的卡顿，影响用户体验。
        
        - 懒加载消息
        - 懒加载图片

      - 接入人工分类

        接入人工分类为用户提供了选择问题分类的渠道，在确保用户能够正确的接入相应的客服队列

        该分类接入支持搜索所有分类，方便用户能够快速找到所要找的分类

      - 消息提醒强化

         消息提醒强化主要功能在于当用户离开当前在线客服页面后，能够保证客户仍然能收到来自客服的消息提醒。这是通过系统api的Notification实现

      - 排队信息优化

         当用户接入队列繁忙，达到客服接入队列上限的时候，就会进入到排队状态，直到客服主动接入会话或者客服队列不繁忙了自动接入

      - 评论功能

         用户评论本次服务等级，做出反馈，收集数据后可供分析以及改进服务

   - 形成了一个闭环的系统

      从用户的登录
      到智能客服
      再到接入队列
      之后的在线客服
      到结束会话
  
   - 从上线至今的各种做过的统计数据

     - 从7.6灰度上线以来，在线客服访问量会话为xxx 

     - 接入人工客服后闭环率达到75%，为工单减少了一半以上的服务量，五星好评率也达到了96%，受到了用户的广泛好评

     - 关键词介绍
       - 会话满足量：不点踩、不提单、不打电话、非间接回答的 会话量
       - 闭环率：直接在在线客服解决，不提单
   - 性能优化的存点

     在性能方面，现在采用的是SPA进行构建，但是spa存在以下缺点
     - 首页渲染白屏时间长 
     - seo指数很好

     采用了以下方案来进行性能优化

     - 使用预渲染进行优化：通过 prerender-spa-plugin, 原理是开启 puppeteer（谷歌发布的无头浏览器，可以理解为一个通过 api 调用的 chrome），爬取静态的html节点，形成dom树，而不是像单纯spa那样只有单纯的一个根节点，剩余其他的都交给js进行渲染
     - 资源优化：

     - 接下来方案可能考虑采用
       - 对JS文件进行拆分，使组件按需加载
       - ssr 控制dom大小，
  
   工单系统 

    - 简介

      工单系统是客户处理工单的一个后台系统，主要氛围工单列表、提交工单、自助工具、服务授权

    - 灰度入口

      为更好的支持腰部客服，以最小风险的上线在线客服版本，同时上报用户数据，支持热门问题、热门标签配置以及数据统计，增加灰度入口

    - 重构系统

      现工单系统采用vue+qcvue搭建，运行已久，缺乏维护；而官网控制台侧现在主流推行react+tea2.0，为了更好的接入官网控制台，对旧项目进行维护，重构工单项目。由于我们团队之前也还没做过使用tea接入，所以我使用react+typescript+tea搭建了项目初期的demo，并对tea框架的接入进行了初步的尝试和踩坑，相关接入指引之后会做一套新的km分享出来方便大家后续一起搭建项目
      
      上线后引流数量 比例

      7.20发布以来

   km:两篇 对于智能客服的部分技术记录及整理
   
2. 加入团队的感受

    1. 开会的那一次

       前三个星期，召开了第一次前端组的组会，主要事项是和重庆的小伙伴们讨论安灯等项目接入的问题，在开会的过程中，我们讨论了安灯前端的业务以及代码架构及封装上的一些实现方式。由于初期在开发的时候，我们组主要是标哥一个人solo安灯整个项目，所以在开发过程中，对于框架进行了一定程度上的二次封装以及修改，但是尚未有完整的文档接入。但是自从有重庆的同学一起加入到我们团队以来，我们团队的开发人员一下子多了起来，所以对统一开发要求也更高了。同时通过我们对于安灯业务的介绍，也才开始更加深入理解我们中心的主要职责：为用户提供完善的售后服务，对用户的问题能够快速响应、解决，提高用户对腾讯云产品的信任，为腾讯云产品保驾护航。


    2. 在团队中有丰富的技术收获

         - 对于之前学习的很多知识有了落地应用的机会
         - 接入云函数进行快速开发，极大的提高了开发效率
         - 在许多没有参与的项目中，即便只是阅读项目的代码、了解项目的实践目标及开发过程中的难点后，也能从中学到很多

    3. 团队是一个温暖的大家庭

       不止于一起完成任务，我们会有团建、每个月的生日会，也会有在项目上线前大家一起在会议室里紧急加班到十点多，我们团队也对新人很照顾，让新人能够迅速融入团队、投入工作。遇到问题的时候，积极的向我们的团队成员请教，都会很耐心详细的解答我的疑问

3. 收获与心得、未来学习计划

    技术收获
    1. react hook + typescript 技术栈
    
       之前一直有听说这套技术栈但是一直没有在项目中去运用开发过，使用后确实非常好用非常喜欢

    2. 通过 SSR 和 预渲染 进行性能优化
    3. 通过 web socket 建立通信
    4. 简易富文本框实现思路
    5. 怎么去做一个灰度

    非技术的收获
    1. 沟通能力

       作为一个前端开发，我们需要同时与后端、测试、产品等进行对接，如何在最短时间内让对方明白你的意思，减少沟通成本，实践总结下来，多通过文档/tapd工具进行沟通

       我们部门的职责就是为客户提供更好的服务，保障完善客户完整的售后体验从这一点出发，就可以理解很多产品的考虑

       在工单系统灰度上线在线的时候，经过与产品的沟通，我的初期方案就直接往最终的实现方案开发了，但是在联调的时候发现，后端并没有来得及按最终方案实现，而是采取了一个折中的过度方案，然后我就只能

       在交付过程中，由于测试环境上的问题会产生各种不一样的情况，一开始我都是自己和产品or测试沟通，但是发现效率很低，于是就利用tapd直接写说明，一劳永逸。
         
    2. 熟悉了完整的研发流程 

       需求 开发 联调 部署测试环境 验收 测试 预发布 发布正式环境
    
    3. 更好的规划自己的时间分配 努力做一个时间管理大师

       保证高效开发的同时，也有时间对自己的业务进行思考，进行技术沉淀
       一个不是时间管理大师的开发不是好开发

    4. 在团队中认识了很多有趣的灵魂（群里聊天也能学到很多知识.jpg）

       php 从入门到放弃 c++ 从看懂到看开 mysql从删库到跑路  sudo rm -rf ./

    未来计划
    1. 前端技术日新月异，唯有不断学习才能保证与时俱进。继续学习前端，跟进前端技术的发展，前端技术更新起来是非常快的。结合我们团队的业务探索可能在我们项目中进行实战的技术。

    2. 打磨产品

      不止步于完成需求，应该思考如何把产品做的更好，在工作中时刻记住“死磕自己，愉悦别人”的精神

    3. 培养自己对业务的敏感性，当前经验积累不足，对于一些没有接触过的需求没办法马上找到很好的技术方案进行实现，产品的思维，让自己能更好的理解业务需求以及用户的诉求，以提高用户体验、为用户提供更好的服务为目标来开发

    4. 积极与团队其他成员交流，向大家学习，了解团队内其他项目，交流探讨实践中使用的技术栈及技术难点，从中学习，做分享会，技术沉淀，与团队共同提升

4. 对导师和团队的反馈和建议

    1. 希望能继续我们团队内部的每周的分享会

       每周的前端分享组会，有利于我们团队技术的提升，将我们在业务中的尝试作为我们团队的技术沉淀，

       为什么会有这个想法呢？是因为我们刚刚讲的第一次前端组会上，标哥分享了他封装andon模块的思路，会后我也去看了标哥封装的代码，那套思路和我在另一个开源项目上很像，跟标哥讨论了一下封装的方案，在这个过程中学到了蛮多东西的，而且就是我们那次会议也就这个问题展开了一些讨论，在这个问题学到很多

       另一个就是玉飞之前写的他做的日志上报的思路，就是我读完他的km后还是没用很明白，因为是之前没有怎么接触过的领域，我觉得还是蛮需要这种每周分享的，
    
       有利于熟悉我们团队的业务以及积累我们自己的技术沉淀

    2. 感谢团队与导师

       感谢遇见我们这么好的一个团队，在这段短暂的实习期学到了很多东西，不止于技术上的东西，还有很多技术之外的收获

       感谢导师在这段时间对我的指导，即使有时候我会犯傻问一些看起来很蠢的问题，better还是会很详细耐心的解答我的困惑，而且better也给我树立了很好的一个榜样，能够快速的理解业务并高效提出可行的解决方案，我经常看到better在休息时间，他还在研究掘金，保持学习并把新技术应用到项目中，这是我觉得我做的比较不足的

