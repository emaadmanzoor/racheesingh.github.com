---
layout: post
title: "Annotated Map Plots"
description: ""
category: 
tags: []
---
{% include JB/setup %}
It was getting hard to debug the code which was calculating the networks allocated to each Voronoi cell. So I added annotations to the map to make it easy to decipher which server is named what.

Here is how the annotated map looks:
<img src="https://github.com/racheesingh/voronoi-map-py/raw/master/1.png" title="Buckets of Networks" align="left" width="100%"/>

And zooming into the cluttered regions:
<img src="https://github.com/racheesingh/voronoi-map-py/raw/master/2.png" title="Buckets of Networks" align="left" width="100%"/>

<img src="https://github.com/racheesingh/voronoi-map-py/raw/master/3.png" title="Buckets of Networks" align="left" width="100%"/>


## The Key
Here is how the numbers displayed on the map relate to the server names:
     	  ```  
          0 : http://vobox.ihep.ac.cn

     	  1 : http://squid-cms.lip.pt, http://squid01.ncg.ingrid.pt

	  2 : http://frontier.iihe.ac.be

	  3 : http://squid.ihepa.ufl.edu, http://squid2.ihepa.ufl.edu

	  4 : http://grinr06.inr.troitsk.ru

	  5 : http://cmst0frontier.cern.ch, http://cmst0frontier1.cern.ch, http://cmst0frontier2.cern.ch

	  6 : http://squid04.pic.es, http://squid03.pic.es, http://squid02.pic.es, http://squid01.pic.es

	  7 : http://frontiercache.esc.qmul.ac.uk

	  8 : http://F01-010-116-e.gridka.de, http://cmssq1-fzk.gridka.de, http://cmssq2-fzk.gridka.de, http://F01-010-115-e.gridka.de

	  9 : http://squid01.grid.sinica.edu.tw, http://squid02.grid.sinica.edu.tw, http://lcg00114.grid.sinica.edu.tw

	  10 : http://lcg45.sinp.msu.ru

	  11 : http://squid-cms-3.cr.cnaf.infn.it, http://squid-cms-2.cr.cnaf.infn.it, http://squid-cms-1.cr.cnaf.infn.it

	  12 : http://farmsrv.ts.infn.it

          13 : http://squid.lnl.infn.it

          14 : http://squid2.cmsaf.mit.edu, http://squid.cmsaf.mit.edu, http://squid1.cmsaf.mit.edu

          15 : http://pccms26.ba.infn.it, http://cofin2003.ba.infn.it

          16 : http://cache02.hep.wisc.edu, http://cache01.hep.wisc.edu, http://frontier02.hep.wisc.edu, http://frontier01.hep.wisc.edu

          17 : http://proxy-1.t2.ucsd.edu

          18 : http://grid02.physics.uoi.gr, http://grid01.physics.uoi.gr

          19 : http://144.16.111.46

          20 : http://muon.grid.kiae.ru, http://se1.itep.ru

          21 : http://higgs.fis.cinvestav.mx

          22 : http://ndcms.crc.nd.edu

          23 : http://frontier.sprace.org.br

          24 : http://ingrid-monbox.cism.ucl.ac.be

          25 : http://osg-gate.rice.edu

          26 : http://cluster144.knu.ac.kr

          27 : http://silo3.hip.helsinki.fi

          28 : http://fs1.accre.vanderbilt.edu, http://fs2.accre.vanderbilt.edu

          29 :http://cms-vo.polgrid.pl

          30 : http://lcgcalali.ciemat.es

          31 : http://cmssquid.pi.infn.it, http://cmssquid2.pi.infn.it

          32 : http://cmsrm-frontier.roma1.infn.it

          33 : http://cmscache00.hep.ph.ic.ac.uk, http://cmscache01.grid.hep.ph.ic.ac.uk

          34 : http://pcncp04.ncp.edu.pk

          35 : http://cmsvobox.lcg.cscs.ch

          36 : http://umiss005.hep.olemiss.edu

          37 : http://io.hep.kbfi.ee

          38 : http://ruhex-squid.rutgers.edu

          39 : http://squid.rcac.purdue.edu, http://osg.rcac.purdue.edu

          40 : http://hurr.tamu.edu

          41 : http://grid158.kfki.hu

          42 : http://uscms1-se.fltech-grid3.fit.edu

          43 : http://squid1.ppgrid1.rhul.ac.uk

          44 : http://cmsfrontier3.fnal.gov, http://cms-xen19.fnal.gov, http://cmsfrontier4.fnal.gov, http://cmsfrontier2.fnal.gov, http://cmsfrontier1.fnal.gov

          45 : http://cmsgrid.oeaw.ac.at

          46 : http://hepcms-hn.umd.edu

          47 : http://mirror.hep.by

          48 : http://cclcgcms01.in2p3.fr, http://cclcgcms02.in2p3.fr

          49 : http://hugin.hpcc.ttu.edu

          50 : http://cmsfrontier.marie.hellasgrid.gr

          51 : http://grow-prod.its.uiowa.edu

          52 : http://red-squid1.unl.edu, http://red-squid2.unl.edu

          53 : http://cms-dm.cac.cornell.edu

          54 : http://agent.tier3.ucdavis.edu

          55 : http://t3frontier.psi.ch

          56 : http://lcgsquid01.gridpp.rl.ac.uk, http://hepsquid02.pp.rl.ac.uk, http://lcgsquid02.gridpp.rl.ac.uk, http://hepsquid01.pp.rl.ac.uk, http://cms-squid.gridpp.rl.ac.uk

          57 : http://grid-squid2.physik.rwth-aachen.de, http://grid-squid1.physik.rwth-aachen.de

          58 : http://frontier.ulakbim.gov.tr

          59 : http://hepgums.colorado.edu

          60 : http://sbgce2.in2p3.fr

          61 : http://nat005.gla.scotgrid.ac.uk

          62 : http://glite-mon.ceres.auckland.ac.nz

          63 : http://t2-cms-db1.desy.de, http://t2-cms-db0.desy.de

          64 : http://lcgsqd.jinr.ru

          65 : http://cms-gate.kipt.kharkov.ua

          66 : http://grid009.gridc.lip.pt
```