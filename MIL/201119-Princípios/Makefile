PREF=201119-Fundamentos

clean:
	for TRG in ${PREF}; do \
		for EXT in log aux blg bbl nav out snm toc; do \
			rm -vf $$TRG.$$EXT; \
		done; \
	done

wipe: clean
	rm -vf fig/*pdf

res/logo/%.pdf: res/logo/%.svg
	inkscape \
		--export-type=pdf \
		--export-filename=$@ \
		$<

${PREF}.pdf: ${PREF}.tex \
		res/cc/by-nc-nd-88x31.pdf \
		res/logo/BibliaShare.pdf
	pdflatex ${PREF}.tex

${PREF}.png: ${PREF}.pdf
	mkdir -p ${PREF}.png
	cd ${PREF}.png; \
		pdftoppm -png -forcenum -r 304.76 "../${PREF}.pdf" "${PREF}"

201125-Fundamentos.pdf: ${PREF}.pdf
	pdftk \
		A=$< \
		cat A1 A10-12 A21-39 \
		output $@

