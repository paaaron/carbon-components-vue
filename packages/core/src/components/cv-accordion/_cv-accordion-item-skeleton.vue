<template>
  <li :class="itemClasses">
    <button disabled type="button" :class="`${carbonPrefix}--accordion__heading`">
      <ChevronRight16 :class="`${carbonPrefix}--accordion__arrow`" />
      <cv-skeleton-text :class="`${carbonPrefix}--accordion__title`"></cv-skeleton-text>
    </button>
    <div :class="`${carbonPrefix}--accordion__content`">
      <slot></slot>
    </div>
  </li>
</template>

<script>
import CvSkeletonText from '../cv-skeleton-text/cv-skeleton-text';
import ChevronRight16 from '@carbon/icons-vue/es/chevron--right/16';
import carbonPrefixMixin from '../../mixins/carbon-prefix-mixin';

export default {
  name: 'CvAccordionItemSkeleton',
  mixins: [carbonPrefixMixin],
  components: {
    ChevronRight16,
    CvSkeletonText,
  },
  props: {
    open: { type: Boolean, default: false },
  },
  computed: {
    itemClasses() {
      const classes = [`${this.carbonPrefix}--accordion__item`];
      if (this.open) {
        classes.push(`${this.carbonPrefix}--accordion__item--active`);
      }
      return classes.join(' ');
    },
  },
};
</script>
