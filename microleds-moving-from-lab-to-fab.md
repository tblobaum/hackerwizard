---
title: MicroLEDs Moving From Lab to Fab
menu_order: 1
post_status: publish
post_excerpt: ''
slug: microleds-moving-from-lab-to-fab
taxonomy:
  category:
    - hacker-news
  post_tag:
    - HN
custom_fields:
  ttr: 522
  source: Semiconductor Engineering
  url: 'https://semiengineering.com/microleds-moving-from-lab-to-fab/'
---
Every disruptive technology has its “aha” moment — the time when everyone from engineers to investors realizes that, yes, this technology is the real deal and it won’t be scrapped on the R&D floor.

For many, it was Samsung’s recent announcement of a 110-inch microLED TV that irrevocably put microLEDs on the map. The TV’s price is $155,000, but as with most consumer electronics that go mainstream, economies of scale will sharply reduce that amount.

“It signaled that microLED TVs are coming, but lots of engineering advances and disruptive technologies are needed first to reduce cost by 20X to 30X for mainstream adoption,” said Eric Virey, Ph.D., senior industry analyst at Yole Développement. Some of the first commercialized microLED displays will be for near-eye augmented reality/virtual reality or mixed reality applications for head-up displays or glasses.

![](https://i0.wp.com/semiengineering.com/wp-content/uploads/MicroLEDFig1.jpg?resize=1591%2C1075&ssl=1)  
**Fig. 1: Combining CP Display’s IntelliPix driver/backplane architecture with Global Foundries’ FDX 22 nm silicon-on-insulator (SOI) process platform, 1:1 full color AR/MR microdisplay with 3 µm microLEDs will soon begin production. Source: CP Display**

MicroLEDs have outstanding performance attributes. The offer higher pixel density, lower power consumption, faster (nanosecond) response time, and wider viewing angle than LED-backlit liquid crystal displays (LCDs) or organic LED (OLED) displays. Importantly, they offer an order-of-magnitude higher luminance than OLED displays or LCD in direct sunlight conditions, which is crucial for handheld devices, as well as a key enabler for near-eye displays.

The end products fall into three categories:

*   Large displays for TV, signage, and cinema;
*   Medium-sized displays for tablets, automobile headlights, smart phones, and watches, and
*   Microdisplays (Figure 1) for AR/VR/MR applications.

MicroLEDs are just that — microscopic versions of the LEDs we use today. MicroLEDs (<50 µm design rules), miniLEDs (>50 µm and <1 mm) and LEDs (>1 mm) all work in the same way. When current is applied at appropriate voltage, electrons and holes recombine in the active region of the device (the quantum wells), and photons are emitted. The light’s brightness is a function of applied current, but the emitted color (wavelength) is determined by the difference in energy levels of the conduction and valence bands of the semiconductor materials, with AlInGaP used for red LEDs and InGaN used for green and blue LEDs.

LEDs are directly emissive unless the light is converted using phosphor particles or quantum dots. For instance, white light uses blue LEDs with a yellow phosphor coating to make the white we see in lightbulbs, streetlights, auto headlights, etc. Most LEDs today are fabricated on 100 mm and 150 mm sapphire wafers, though InGaN-on-silicon is gaining in popularity, especially among large silicon-based foundries. Historically, LEDs are assembled in a surface-mount technology (SMT) package, wire bonded in place and encapsulated with epoxy or silicone. The key difference with microLEDs is they are used in bare die form rather than in packages. This difference, along with much tighter design rules, makes fabrication of microLEDs a very costly endeavor.

**Yield and transfer technologies**  
As the industry transitions from today’s miniLEDs to microLEDs, foundries and fabs must step up their game considerably.

“Achieving the performance and cost point for microLEDs will require a paradigm shift towards a semiconductor manufacturing mindset,” said John Robinson, senior principal scientist at [KLA](https://semiengineering.com/entities/kla-tencor/).

Robinson pointed to the need for extremely high microLED yields compared to conventional LEDs, including high driver IC and backplane assembly yields, which requires end-to-end fab-wide defect management strategy. In addition to in-line yield management improvements, microLEDs currently do not have a production-worthy process for quickly transferring microLEDs from wafer to interposer or wafer to backplane. This process, a full-scale replacement of pick-and-place tools, is currently a great limiter to the manufacturability of microLEDs.

![](https://i1.wp.com/semiengineering.com/wp-content/uploads/MicroLEDFig2-scaled.jpg?resize=2560%2C1440&ssl=1)  
**Fig. 2: To meet the near-zero tolerance for bad pixels, LED fabs are stepping up their inline metrology, automated optical inspection, and testing protocols. Source: KLA**

From the wafer processing side, Srinivasa Banna, vice president of MicroLED R&D, Lumileds said that in addition to reducing defectivity, which contributes directly to yield, microLED fabs must maintain very tight wavelength uniformity control on both the epi wafer and across the finished panel.

On the testing front, Banna added that while many solutions exist to do photoluminescence-based (PL-based) testing, which measures the spectral properties of the light, including desired wavelength, at epi and processed wafer levels, wafer-level testing of electroluminance (EL) is badly needed. “The ultimate proof is whether the LED lights up properly or not. We want to be able to a-priori mark the bad microLEDs, or the ones with insufficient light emission, and selectively choose the known-good-die for transfer to the backplane.” In lieu of wafer-scale EL testing, test structures provide data, “but this really only gives us a go/no go response,” he said.

Other problems are typical of early-stage technologies. “One of the greatest challenges is the lack of standard manufacturing flows and the diverse range of approaches that are being taken. This leads to a lack of scale to drive equipment development for high-volume manufacturing,” said David Haynes, managing director of strategic marketing at [Lam Research](https://semiengineering.com/entities/lam-research/). “In the short term, we expect to see increased commercialization of small, high-brightness microLED displays in AR/VR and other consumer products such as smart watches, as well as microLED light engines for automotive displays and large-area projection.”

Haynes noted, however, that the timeline for commercialization of large area displays on TFT panels “will depend on how quickly the industry develops mass transfer technologies that can deliver high accuracy and exceptional reliability.” Indeed, Apple’s latest iPad, which uses white miniLEDs for backlighting, requires the accurate placement of 10,000 emitters, which sounds challenging enough. Positioning 25 million red, green, and blue subpixels on a 78-inch TFT panels for a 4K TV, with a tolerance of only 10 non-functioning pixels, will require an exceedingly robust, highly accurate transfer method.

**Different Paths to RGB**  
The difficulty of mass transfer and performance issues as microLEDs scale has led companies to pursue different paths to obtaining red, green, and blue light on the same panel. There are also the differences in drive voltage between red (1.7V threshold voltage), green (Vt of 2.2 V) and blue (Vt = 3.3 V), which complicates the design of driver circuitry. All this can be simplified by fabricating only blue microLED wafers and adding phosphor or quantum dot color converters to make red and green.

However, Lumileds’ Banna said there are tradeoffs to down-converting, as well. Often, some blue bleeds through the converters, and any down-conversion reduces brightness. Quantum dots are semiconductor nanocrystals that can produce monochromatic red, green and blue light and therefore have the potential to be used in future microLEDs. However, today’s QDs are used in layer form to improve the brightness and color gamut of LED-backlit LCDs.

**MicroLED Process Flow**  
The front end of the microLED process begins by growing the epi stack on wafers via vapor phase epitaxy in metal-organic CVD tools (MOCVD). The wafers are then automatically inspected for defects and photoluminescence (PL), or spectral properties are measured.

Next, lithography patterning defines the N and P contact pads, followed by transparent indium tin oxide (ITO) deposition, which spreads the current across the surface of the device. Reactive ion etching (RIE) then exposes the contact pads. The wafer is flipped onto a flexible film, laser lift-off removes the substrate, followed by flipping again, measuring PL and EL and creating a known-good-die map. Next, hundreds or even thousands of microLEDs are transferred via stamp process, laser process, or other means (explored below), and bonded to a separately manufactured TFT or CMOS backplane that contains matching electrical contacts and control circuitry to that on the chip.

SMT bonding processes, using solder deposition and reflow, bond the chips to backplane, followed by AOI, PL, and EL testing again. If defective chips are found, lasers can be used to remove and replace the bad die (called repair), followed by final test of the display including electroluminescence and photoluminescence.

MicroLEDs will require Class 100 cleanroom (less than 100 particles per ft3, ≥0.5 µm), a switch to processing on 200 mm sapphire wafers, scaling of epitaxial processes (MOCVD) to 200 mm, upgrading from mask aligners to i-line wafer steppers for patterning, and single-wafer 200 mm tools for RIE, electroplating, wafer stripping, and perhaps wafer cleaning as well. Most crucially, these tools must employ tight process controls using SPC and newer artificial intelligence programs.

“The end product really drives our specifications for wavelength, film thickness, leakage current, and homogeneity,” said Ajit Pananjpe, CTO at Veeco. He noted that many of the new products being announced require wavelength variability within 2 nm. “Right now, we are close to meeting the wavelength uniformity specifications, and this is not likely to be a show-stopper for microLEDs.”

Optimizing wafer-level processes will be critical to ongoing improvement of microLED performance metrics such as the internal quantum efficiency (IQE), which is how efficiently electron/hole combinations in the device convert to luminance, and external quantum efficiency (EQE), which is how efficiently the device converts electrons passing through the LED to luminance. Up until a couple years ago, EQEs of red, green, and blue microLEDs were in the single-digit range. However, materials and device engineering have improved EQE to the double-digit range for blue, green and AlInGaP red microLEDs, with further improvements needed.

Wafer-level processing of LEDs often targets ongoing improvements of IQE and EQE. For instance, Lam is developing ultralow damage GaN etch processes, GaN structuring processes, and post-etch sidewall damage repair and passivation for improved device performance.

“We’re combining low power, steady state plasma etches with atomic layer deposition in the same module. These processes combine high throughput with the ability to significantly reduce plasma damage of the [GaN](https://semiengineering.com/knowledge_centers/materials/gallium-nitride/) surface,” Lam’s Haynes said. “On the deposition front, we have low-hydrogen silicon nitride passivation solutions, and in order to support compatibility with CMOS foundries, we are developing single-wafer cleaning solutions that are capable of managing gallium contamination on fragile wafers.”

**MiniLED learning**  
MiniLEDs are in volume production today for applications in tablet backlights and keyboard backlights. To speed assembly, Rohinni developed a bond-head that dramatically improves on pick-and-place by positioning the target substrate much closer to transfer substrate and integrating 3D metrology for positioning feedback. The process has been commercialized on the Pixalux bonder from K&S. Here, the miniLED is flipped onto a flexible adhesive film and the substrate is removed. The film is flipped again and placed over, but in close proximity to the target substrate. The bond-head utilizes a high-speed pin actuator to transfer the chip at throughput up to 100 chips/sec.

CyberOptics’ SQ3000 multi-function 3D metrology tool has been integrated with Rohinni’s transfer method to ensure accuracy and repeatability of the alignment process. The metrology system’s proprietary Multi-Reflection Suppression (MRS) sensor technology uses phase-shift profilometry that collects data from a single optical projector and multiple cameras for 3D measurement. The system’s algorithms inhibit reflection-based measurement distortions to allow high accuracy at process speeds of several seconds.

“Given the similarity of miniLED placement with SMT bonding, it’s no surprise that the adoption of tools such as ours is bringing production-worthy results,” said Subodh Kulkarni, president and CEO of [CyberOptics](https://semiengineering.com/entities/cyberoptics/). “For miniLED placement, the system tracks minute deviations from the expected digital signature in x, y and z directions and quickly signals where there is a problem,” he added.

Rohinni, whose tool can be used on any assembly tool, is platform-agnostic, according to Rohinni CTO Justin Wendt. “We see ourselves really as a type of systems integrator, bringing a technology solution for a particular product, in this case miniLEDs, to the tool makers and end uses who can best utilize it,” he said.

**Mass transfer assembly**  
MicroLED mass transfer options include adhesive stamp transfer, laser-assisted transfer, electrostatic transfer, roll-based transfer, and fluid self-assembly. Though many techniques work (see figure 3), a transfer yield of 99.9999% (six 9s or 1 ppm), is needed for volume manufacturing. “Transfer technology is a greenfield today. Manufacturer cannot afford to transfer dead microLEDs, and even though repair strategies exist, they are too laborious and costly for use in volume manufacturing,” said Veeco’s Pananjpe.

![](https://i2.wp.com/semiengineering.com/wp-content/uploads/MicroLEDFig3.jpg?resize=1278%2C852&ssl=1)  
**Fig. 3: A wide variety of methods are being explored to effect mass transfer of thousands of microLEDs simultaneously. Source: “From Lab to Fab: Challenges and Requirements for High-Volume MicroLED Equipment, Yole Développement, Display Week, May 2021**

Perhaps the most mature transfer option, according to Yole Développement’s Virey, uses a polymer stamp to move thousands of LEDs, such as in X-Celeprint’s Micro Transfer Printing process. Each stamp is custom fabricated from injection-molded polydimethylsiloxane (PDMS) and consists of glass backing (for rigidity), a smooth PDMS layer and PDMS “posts” that are lithography-defined and etched for high accuracy in placement. An adhesive ink grabs an array of microLEDs, and printing is performed using laser or other means.

X Display Co., the sister display company to X-Celeprint, recently delivered its first 300 mm transfer tool, and it licenses many of its technologies for microLED manufacturing. Stamp transfer processes are proving reliable, scale-able and capable of high throughput, but further process optimization is needed to achieve six 9s yield.

Laser-assisted mass transfer is offered by 3D-Micromac AG and Coherent. Laser lift-off works by ablating a microscopic layer of GaN, which forms an expanding nitrogen gas layer to enable lift-off. Laser-assisted lift-off is commonly used to remove the sapphire substrate from the processed microLED wafer. At the microdevice or small field sizes, multiple high-energy laser pulses can be used to transfer groups of microLEDs with high accuracy (±1.5 µm). While known for good selectivity and reliability, laser-assisted transfer methods are currently limited to small areas and require further development to speed throughput.

ELux Display pioneered a novel fluidic self-assembly process (see figure 4), which uses active-matrix substrates from a conventional LCD fab. Using a substrate with wells only slightly larger than the microLEDs, liquid containing pretested microLEDs is applied to the surface, and oscillation motion encourages the LEDs to settle in the wells in a highly accurate and unform manner. Fluidic assembly randomizes the microLEDs in liquid, which prevents the mosaic patterns caused by epi wafer nonuniformity.

![](https://i1.wp.com/semiengineering.com/wp-content/uploads/MicroLEDFig4.jpg?resize=1084%2C802&ssl=1)  
**Fig. 4: The fluidic assembly tool from eLux Display positions 518,400 microLEDs (40 µm in size) on a 12.3-inch display in around 15 minutes. Some 33 microLEDs required repair.**

The microLEDs are fabricated from conventional blue LED wafers as flip chips with anode and cathode electrodes arranged as concentric rings on the surface. Prior to assembly, the microLEDs are tested using microPL mapping for shorted die or low EQE devices and optical inspection for process defects or contamination. The ELux’s advantage, relative to deterministic systems using lasers or other methods, is that fluid assembly is designed to harvest only known-good-die. As a result, defects never enter the display manufacturing process.

**Conclusion**  
MicroLED is extremely promising as the next-generation flat panel display technology because it outperforms OLED displays and LCDs in terms of efficiency and response time, while delivering greater luminance, an especially critical feature for electronics used in sunlit conditions. Bringing the cost down and yield up to the levels required for volume production is particularly challenging, especially in the case of mass transfer tools, which are being built from scratch.

LED fabs will necessarily come to resemble high-volume silicon fabs, with end-to-end yield management and more advanced process control. At the wafer level, testing for electroluminance in addition to photoluminance is necessary to fabricate near-perfect displays.

_**Related**  
[Recovery In Flat-Panel Display Biz](https://semiengineering.com/recovery-in-flat-panel-display-biz/)  
Stay-at-home economy boosts demand, more capacity being built.  
[MOCVD Vendors Eye New Apps](https://semiengineering.com/mocvd-vendors-eye-new-apps/)  
VCSELs, mini/microLEDs, power and RF devices point to another boom for this technology.  
[MicroLEDs: The Next Revolution In Displays](https://semiengineering.com/microleds-the-next-revolution-in-displays/)? (2019)  
Technology offers improved brightness, colors, and lower power, but they’re expensive and difficult to manufacture._
